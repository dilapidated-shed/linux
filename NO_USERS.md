# No-users Linux

This fork defaults to a single-user kernel by setting `CONFIG_MULTIUSER=n`.

Linux still retains numeric credential fields internally. Every process runs as UID 0
and GID 0 with all capabilities. UID-, GID-, and capability-changing system calls
are compiled out. User namespaces must also remain disabled in a no-users build.

## Build gate

After generating a configuration:

```sh
make defconfig
scripts/config --disable USER_NS
make olddefconfig
grep -qx '# CONFIG_MULTIUSER is not set' .config
grep -qx '# CONFIG_USER_NS is not set' .config
```

Then build and boot the kernel with a minimal initramfs. The acceptance program
must check:

- `getuid()`, `geteuid()`, `getgid()`, and `getegid()` all return 0;
- `setuid`, `setgid`, and `capset` are absent (`ENOSYS`);
- PID 1 can mount `proc`, start one child, wait for it, and power off.

This first cut removes multiple identities, not the credential structs themselves.
Deleting those structs is a later mechanical simplification after the boot gate is
stable.

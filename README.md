# aMSN Escargot

This repository contains a fork of **aMSN 0.98.9**, an open-source instant messaging client written mainly in Tcl/Tk. It is adapted to connect to **Escargot**, a community service compatible with MSN Messenger: Escargot servers are used as defaults, along with the MSNP12/TWN sign-in flow. This is a client, not a server; you need a valid Escargot account to sign in.

The code retains native components and packaging tools from the legacy aMSN project. Build and packaging requirements may vary with your operating system and Tcl/Tk version.

## Requirements

- Tcl/Tk 8.5 or later, including development headers to build the native extensions.
- C and C++ compilers, `make`, and standard build tools.
- PNG, JPEG, and zlib development libraries for the image extensions.
- **TclTLS** for secure authentication and dispatch connections. It is a separate Tcl package; without it, sign-in may fail.

On Arch Linux, typical build dependencies are `base-devel`, `tcl`, `tk`, `libpng`, `libjpeg-turbo`, and `zlib`. TclTLS is available from the AUR as `tcltls`; install it with your preferred AUR helper. Package names may differ on other distributions.

## Build on Linux

From the repository root, run:

```sh
cd amsn-0.98.9-src
./configure
make
```

To run the client without installing it:

```sh
./amsn
```

To install it under the prefix detected by `configure` (usually `/usr/local`):

```sh
sudo make install
```

If `configure` reports missing Tcl/Tk files or libraries, install the corresponding development packages. If the build succeeds but sign-in reports a TLS error, make sure TclTLS is installed for the same Tcl installation used to run aMSN.

## Quick check

1. Start aMSN with `./amsn`.
2. Check that the selected protocol is MSNP12 and the server points to Escargot.
3. Sign in with an Escargot account and verify TclTLS loads successfully.

User configuration and profiles are stored outside the repository, in aMSN's per-user data directory.

## License

aMSN is distributed under the GNU General Public License, version 2 or (at your option) any later version. See [`LICENSE`](LICENSE).

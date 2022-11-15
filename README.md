# sbdiff

Determine whether two built packages contain the same code, ignoring any
secureboot-related signatures present on their contents.

This allows vendors to safely avoid the maintainance and signing process for a
custom boot stack when there is no advantage to doing so.  Concretely, if
DownstreamDistro rebuilds and reuses the boot packages (or even the whole
system) from UpstreamDistro, they can instead:

1. Rebuild each package normally, which will result in packages not yet signed
   for secureboot.
   
2. Use sbdiff against the corresponding signed package from UpstreamDistro to
   check that the build reproduced successfully.
   
3. Ship the package with the signatures from UpstreamDistro in
   DownstreamDistro.
   
DownstreamDistro can thus avoid maintaining and protecting secure boot keys at
all, and not need to deal with the shim review and signing process.  There is
also no need for special handling for embargoed issues: fixes from
SourceDistro can be safely be pulled in when available (be that publicly or
during the embargo).

## Usage

Hold up, I have to write this thing first :)

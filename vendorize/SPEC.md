# vendorize file format

The vendorize file format is a simple UTF-8 file. Empty lines and lines the
first non-whitespace character of which is '#' should be ignored. All other
lines take the following form:

    vcs import-path commit-id comment

For example:

    git github.com/hlandau/acme a5facdbc0b4d308fcb69b2015ea6cba965b88267 heads/master

The 'vcs' field specifies a VCS name such as 'git', 'hg', 'svn' or 'cvs'. For
other VCSes, it is suggested that the name be chosen as the name of the command
line tool used to operate it.

The import path is a Go import path which represents a repository. It does not
represent a specific package in that repository. For example, specifying
`github.com/hlandau/acme/acmeapi` is invalid.

An import path must be listed only once.

The commit ID is VCS-specific, but should usually be some sort of cryptographic
hash uniquely representing the commit and all files represented by it.

The comment may be any text, but it is recommended that it be the name of a
branch or tag which provides a human-readable label for the commit. For example
a tag name of 'v1.0.1' or a branch of 'heads/master' could be specified. If there
are uncommitted changes in the repository, indicate this by appending '+'.

If the comment contains a space, anything after that space is further comment
information and should be ignored.

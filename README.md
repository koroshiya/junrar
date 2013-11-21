junrar
======

Fork of junrar by Edmund Wagner: https://github.com/edmund-wagner/junrar

Decryption based on java-unrar: https://code.google.com/p/java-unrar/


Pure Java unrar library that aims to provide a simple API for extracting and reading from RAR archives.

Archives can be tested for encryption, tested for password protection, extracted, or read from directly.


Example usage:


Archive archive = new Archive(new File(location), "test");

boolean encrypted = archive.isEncrypted();

boolean passwordProtected = archive.isPasswordProtected();

/*

Where "location" is the path to a RAR archive, and "test" is the password to use.

eg. location might be "/home/user/test.rar"

or "C:\\file.rar"


Unprotected files require no password. A blank or arbitrary password can be used.


isEncrypted() tests for encryption (whether or not the entire archive requires a password to be read).

isPasswordProtected() tests for both encryption AND password protection on the contents.

Password protection here implies that the file list can be read, but the files cannot be extracted without a password.


*Note: isPasswordProtected will return false if a valid password was passed in.

eg. If test.rar has a password of "test", then

(new Archive(new File("test.rar"), "test")).isPasswordProtected();

would return false, but

(new Archive(new File("test.rar"), "testing")).isPasswordProtected();

would return true.

*/


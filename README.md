# GtkPass
A password generator with GTK-based graphical user interface.

## Usage

_GtkPass_ is a simple password generator with a GTK-based user interface. I wrote it mainly to get in touch with GTK-development and GTK's binding for C++.

_GtkPass_ allows the user to specify the input alphabet for the password which means the generated password will only consist of characters from the chosen alphabet. The user may choose from one or more of the following character sets:

 - Lower case characters (a, b, c, ..., z)
 - Upper case characters (A, B, C, ..., Z)
 - Numbers (0, 1, ..., 9)
 - Dash character (-)
 - Space character ( )
 - Special characters (all printable ASCII special chars without dash and space)

If the user does not select at least one option, the button for starting the password generation will be disabled. The user is also able to choose the password length, of course.

On clicking the "Generate"-button the application will fetch random numbers from `/dev/urandom` or `/dev/random` by using [libsodium](https://github.com/jedisct1/libsodium/) (a fork of [NaCl](http://nacl.cr.yp.to/)). These random numbers will be used to select the characters from the input alphabet and then concatenated to the final password.

An additional feature is the calculation of the theoretical password entropy as a factor of password security. _GtkPass_ calculates and displays the entropy and shows a colored bar indicating the theoretical security the password may provide (entropy is a property generation process, not a concrete password itself; see [crypto.stackexchange.com](https://crypto.stackexchange.com/questions/19620/how-to-calculate-the-entropy-of-passwords)).

## Compiling & Installation

This project is based on the good old `Autotools`. Therefore for compiling and installing the software you only need the commands:

```
./autogen.sh
./configure
make
make install
```

There are a few requirements your system has to meet in order to successfully build the project. I developed and tested the program on Linux only, so there may be problems building on Windows. You will definitely need the following libraries and their respective development headers installed on your system:

 - `libsodium` (for secure random numbers)
 - `libgtkmm-3.0` (C++ binding for GTK)

Compilation will succeed with a compiler compliant to the C++-11 standard, only.

The source files contain Doxygen-style comments for automatic generation of a complete source documentation. The documentation can be generated by executing

```
doxygen
```

in the project's root directory.

## Tests

_GtkPass_ includes unit-tests for its core (non-GUI) components. These are written with the dead-simple testing framework `catch`. The test can be executed with

```
make check
```

## Translations

_GtkPass_ uses `gettext` for translations. The application provides texts for the following languages:

 - English
 - German

## Known Bugs & Problems

Currently there are no bugs or problems that I am aware of. If you find any, please open an issue at [https://github.com/Darth-Revan/GtkPass/issues](https://github.com/Darth-Revan/GtkPass/issues).

## License

This software is provided under the terms of the GNU General Public License Version 3. See the file `LICENSE` for more information.

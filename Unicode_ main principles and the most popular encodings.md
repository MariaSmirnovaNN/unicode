# Unicode: main principles and the most popular encodings
\
Unicode is a universal character encoding system that is used for processing, displaying, and storing written texts in all world languages, both modern and ancient ones. It also defines codes for punctuation marks, technical and mathematical symbols, and many other characters used in writing. The current version of Unicode, 13.0, includes a total of 143,859 characters. 

 Unicode was initially created for unifying all the different encoding schemes in order to avoid the confusion in representing and handlind the texts in different systems of writing. This article contains the information about the history of Unicode, as well as about some advantages and disadvantages of its two most popular encodings, UTF-8 and UTF-16.

### Background and history 

The development of Unicode began in 1987: by the end of the 1980s, it was clear that the existing 8-bit encoding systems were not sufficient for decent text processing. To illustrate the most common issues of that time, let’s take a look at the ASCII standard. 

ASCII was developed back in the 1960s, long before computers and computer software became widespread. It evolved from telegraph code and was based on the English alphabet. Initially, ASCII used a 7-bit encoding scheme, which allowed support of 128 different numbers to encode all standard English letters, uppercase and lowercase letters, as well as punctuation characters and numbers. Later, as computers settled into an 8-bit (1-byte) structure, ASCII was turned into an 8-bit system. 

Characters in ASCII were represented by numbers between 32 and 127, and in the binary format, they were encoded into 7-bit integers. For example, the percent sign (%) in ASCII would be represented by binary `0100101`, decimal 37, and the capital letter A - by `1000001`, decimal 65. The first 128 characters in that system remained intact and were standardized, and the other 128 should have represented some special characters, including characters from other languages. The first 32 codes in it were reserved for control characters that should have been used for controlling devices rather than presenting printable information. 

Though ASCII was quite a versatile system that covered almost all the needs of English speakers, still it was not sufficient to include all the character options and represent all the existing languages. It also created some difficulties even when used for writing in English. Some marks in it that are notionally separate have been unified because of the limitations. This led to many confusions, as such marks as apostrophe, opening single quotation mark, and closing single quotation mark or hyphen and minus were encoded with the same character. 

Besides ASCII, there were other encoding systems, each of which consisted of a unique set of characters. This made it extremely difficult to convert from one system to another or transfer files between devices that run different operating systems. Besides, with 8-bit encoding standards, it was impossible to encode non-alphabetic writing systems or find a place for pseudo-graphic characters, as there was no way to work with more than 256 characters at a time, and the first 128 of them were already taken by universal Latin and control characters. The fonts were also tied to specific encodings that partially or fully duplicated each other. 

To address all of these issues, it was necessary to create a single encoding system that could be used for all known languages across all devices and bring order to the chaos that existed before. And Unicode became such a system. 

### Main principles 

As a starting point, Unicode actually took the ASCII character set: it was already widespread, and it was important to maintain compatibility with that system and lessen the impact of adopting Unicode for ASCII users. Taking this into account, the first 128 characters of Unicode match the ASCII set completely. Now if an ASCII encoded file is opened with Unicode, the characters in it will still be decoded correctly. 

As mentioned above, at the moment the Unicode standard includes codes for all the major written languages, including, besides the European scripts, scripts of Asia, right-to-left Middle Eastern scripts, diacritics, emojis, arrows, etc. What allows such a great variety of symbols to be encoded with Unicode is the very core principle of this system. 

In ASCII, each character was mapped to a certain sequence of bits. In Unicode, instead of it, a character is mapped to something that is called a *code point*. 

The concept of a code point breaks the old idea that there should be a direct one-to-one correspondence between characters and particular sequences of bits. Instead of this, Unicode sees each character as an abstract concept, a sort of Platonic “idea of a character”. These abstract concepts are units of textual data, not glyphs (graphical forms that represent characters in writing) themselves; they are a result of an agreement between people, and they are fixed by the standard. In Unicode standard, there is a code point for each and every character, and the visual rendering of that character (shape, size, style, and font) is left to the software, such as word processors or web browsers. 

Code points have a specific format: they are presented as hexadecimal numbers with the `“U+”` prefix. For example, the percent sign in Unicode is represented by the code point `U+0025` and the capital Latin letter A by `U+0041`. While there are several ways of representing these characters in the computer memory, as well as displaying them using different software, the Unicode standard ensures that these symbols will be recognized the same way by anyone who is familiar with this standard, and they won’t be confused with similar-looking symbols, or, as in the case with the capital Latin letter, with similar-looking letters from other alphabets, such as French, German, or Russian ones. 

The Unicode codespace consists of 1,114,112 code positions in the range 0 to 10FFFF. As at
March 2020, then the 13the version of Unicode was presented, only 143,859 code positions are assigned values. Some of them will never be representing any values: the Unicode consortium promised that they will always be kept intact for private use. It’s done to make it possible for the end users or vendors to assign some code points to their own characters internally, or use them with specialized fonts. 

Almost all the commonly used characters are represented by the first 64 thousand code points. This area of the Unicode codespace is called BMP - “basic multilingual plane”. Planes are large groups of code points, each one including 65,526 of them. Besides the BMP, there are 16 supplemental planes. They include code points for the characters of historic scripts, musical and mathematical symbols, rare characters of some Asian languages, and the abovementioned “private” characters (planes 15 and 16). 

### Unicode encodings 

The Unicode standard supports three encoding forms: UTF-8, UTF-16, and UTF-32. “UTF'' stands for “Unicode Transformation Format”, the algorithm that allows to map every Unicode code point to a unique byte sequence. The numbers in the encodings’ names designate the bit values that are required for representing a character in memory: 16-bit for UTF-16, 32 bits for UTF-32 and 8-bit for UTF-8. 

Both UTF-8 and UTF-16 are variable-length encodings. Each Unicode character in UTF-8 is represented with 1 to 4 bytes, depending on the value of its code point. For UTF-16 it’s 2 to 4 bytes per character. UTF-32 is a fixed-length encoding scheme; it always uses 4 bytes to encode a single code point. 

Let’s take a closer look at the key features of UTF-8 and UTF-16 and their key advantages and disadvantages. 

#### UTF-8

UTF-8 was designed as an alternative to one of the first Unicode encodings, UTF-1. The need for replacement of that recording arose because it lacked some features, such as self-synchronization and fully ASCII-compatible handling of characters (e.g. slashes). 

As mentioned above, UTF-8 uses 1 to 4 8-bit (1-byte) code units for encoding code points. In order to distinguish between single bytes and multi-byte sequences, UTF-8 includes a system of binary prefixes, which uses the high bits of each byte for that purpose. Concatenation of the remaining bits forms the code point index.

The lower the code points numerical values are, the fewer bytes are used for encoding. This allows for the first distinctive feature of UTF-8: its spatial efficiency. The first 256 characters included in the Unicode standard are represented as just one byte. Other characters that are not that widespread and appear in the standard later, are encoded into larger code units. This scheme makes it possible to significantly reduce the file size, as the most commonly used characters take the least volume of memory. 

Such a design also makes UTF-8 endianness independent: the fact that UTF-8 data is represented as a byte stream eliminates the issue with bytes order at its core. 

Another benefit of UTF-8 encoding is its complete backward compatibility with the ASCII character set. UTF-8 is designed in a way that its first 128 characters are encoded using a single byte with the same binary values as in ASCII (bytes 0-127), and therefore map directly. As a result, the majority of text-related software that uses ASCII for formatting and control purposes (text display apps, text processors, parsers, etc.) can work with the UTF-8 byte stream as with a sequence of 8-bit (1-byte) characters without having to decode it, as it would be in case with multi-byte sequences. This makes UTF-8 useful for legacy systems that want to start supporting Unicode at some point as there is no need to make any changes to the way texts are processed. 


The fact that all non-ASCII code points in UTF-8 are encoded using sequences of bytes 128–255, has one more consequence. Since ASCII bytes never occur inside the encoding of non-ASCII code points, lots of widely-used string programming idioms—such as null termination, or delimiters (newlines, tabs, commas, slashes, etc.) are safe to use with UTF-8 strings. 

Besides, UTF-8 is self-synchronizing: character boundaries are easily identified by scanning for well-defined bit patterns in either direction. It’s always possible to resume processing by locating the next valid character if bytes are lost due to error or corruption. The previous valid character can be located easily as well, which allows for shortening strings so that they could fit specified fields. This also implies that UTF-8 can be used along with byte-oriented string-searching algorithms (as a character is the same as a "word" made up of that many bytes), and optimized versions of byte searches can be much faster due to hardware support and lookup tables that have only 256 entries.

The advantages listed above allowed UTF-8 to become the most common encoding in the modern world. As of the year 2020, it is used by more than 95% of all websites. There is also a perception, mainly spread across the Web and Linux communities, that UTF-8 should become a universal encoding for every purpose. However, there are also some downsides. 

First of all, due to its design UTF-8 takes more space in case with non-Latin scripts than specific multi-byte encodings. For example, in some East-Asian legacy encodings two bytes are enough to encode a character, yet UTF-8 requires three bytes per character. Self-synchronization also takes more memory. 

Besides, since UTF-8 is a variable-length encoding, it’s not possible to determine the number of bytes for the UTF-8 text  from the number of Unicode characters. 

There are some compatibility issues as well: many mail gateways and other legacy apps strip the 8-bit chars of UTF-8 because these apps were originally designed as 7-bit ASCII apps. 

#### UTF-16 

UTF-16 is the oldest Unicode encoding form. It uses 1 or 2 16-bit code units to encode code points. 

In UTF-16, characters that are included in the Basic Multilingual Plane (those in ranges `U+0000`—`U+D7FF` and `U+E000`—`U+FFFD`) are stored as a single 16-bits unit. The characters with code points bigger than U+FFFF (non-BMP ones) are encoded with two units, which are called a *surrogate pair*. A surrogate pair includes a high surrogate (in range `U+D800`—`U+DBFF`) and a low surrogate (in range `U+DC00`—`U+DFFF`). Surrogate characters are always written as pairs (high followed by low) and they become invalid when taken singly. 

Such an approach to encoding makes UTF-16 less efficient when it comes to Latin alphabet, but at the same time quite memory-saving in case with non-Latin characters. See for yourself: for the first 128 code points (`U+0000` - `U+007F`) UTF-8 requires 8 bits per character and UTF-16 requires 16. However, for the code points in the range from 128 to 65,535 (`U+0800` - `U+FFFF`) UTF-8 needs 24 bits, while UTF-16 still requires only 16. Therefore, if in the file there are more non-Latin characters than there are Latin ones, UTF-16 is more efficient than UTF-8 and vice versa.

It’s important to underline that since UTF-8 and UTF-16 use different algorithms to map code points to binary strings, these two encodings are not compatible with each other. Being a multi-byte encoding, UTF-16 is not compatible with single-byte ASCII either. Additionally, UTF-16 cannot work with code languages treating NULL as a string terminator because of the fact that UTF-16 strings contain many zero bytes. 

Another important distinctive feature of UTF-16 is that it doesn’t have endianness defined by default, so there is a need to select a byte order when handling UTF-16 files. To assist in recognizing the byte order of code units, the *Byte Order Mark* (BOM) should be added at the beginning of every UTF-16 encoded file or byte stream. BOM is a code point with the value `U+FEFF` (big endian) or `U+FFFE` (little endian). These code points do not encode any valid characters and are used solely for byte order designation. Alternatively, the byte order may be stated explicitly when choosing the encoding type: UTF-16BE or UTF-16LE. In this case, there is no need to add the BOM at the beginning of the file. 

In contrast to UTF-8, UTF-16 is not alway capable of resynchronizing after finding a corrupt or missing byte at the start of the next code point. It cannot handle an odd number of missing bytes - in such a situation, all the following text will be corrupted. However, UTF-16 still can handle altered bytes, which provides quite a reasonable level of protection against corruption. 

UTF-16 is popular in many environments that need to balance efficient access to characters with economical use of storage. For example, it is used as a standard string representation in Javascript, as well as in Python, C#, Qt, and Java. However, due to its incompatibility with ASCII it never gained popularity on the Web. 

Historically UTF-16 is used by Microsoft Windows apps: Microsoft was one of the first companies to implement Unicode, using the encoding scheme UCS-2 at first. Lately it evolved to UTF-16. Typically, a Windows application uses UTF-16 internally, converting only as part of a "thin layer" over the interface that must use another format. This technique defends against loss and corruption of data. 

UTF-16 is popular with the Microsoft Win32 APIs since many of them date back to the time when Unicode was 16-bit fixed width. However, using UTF-16 makes characters outside the Basic Multilingual Plane a special case which increases the risk of oversights related to their handling. At the same time UTF-16 is still the only way to get proper Unicode support in Windows since the 8-bit version of Win32 does not support UTF-8 at the moment. 

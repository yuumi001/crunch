## Crunch

Crunch is a wordlist generator where you can specify a standard character set or a character set you specify. crunch can generate all possible combinations and permutations.

This code can be easily adapted for use in brute-force attacks against network services or cryptography.
  
## usage example

./crunch <min-len> <max-len> [charset]
  e.g: ./crunch 3 7 abcdef
 
  This example will compute all passwords between 3 and 7 chars
  using 'abcdef' as the character set and dump it to stdout.

## usage

  usage: ./crunch <from-len> <to-len> [-f <path to charset.lst> charset-name] [-o wordlist.txt or START] [-t [FIXED]@@@@] [-s startblock]
 
  Options:
  
  -b  : maximum bytes to write to output file. depending on the blocksize files may be some bytes smaller than specified but never bigger.
  
  -c  : numbers of lines to write to output file, only works if "-o START" is used, eg: 60  The output files will be in the format of starting letter - ending letter for example:
                crunch 1 5 -f /pentest/password/charset.lst mixalpha -o START -c 52
                will result in 2 files: a-7.txt and 8-\ .txt  The reason for the
                slash in the second filename is the ending character is space and
                ls has to escape it to print it.  Yes you will need to put in
                the \ when specifying the filename.
  
  -d          : specify -d [n][@,%^] to suppress generation of strings with more
                than [n] adjacent duplicates from the given character set. For example:
                ./crunch 5 5 -d 2@
                Will print all combinations with 2 or less adjacent lowercase duplicates.
  
  -e          : tells crunch to stop generating words at string.  Useful when piping
                crunch to another program.
  
  -f          : path to a file containing a list of character sets, eg: charset.lst
                name of the character set in the above file eg:
                mixalpha-numeric-all-space
  
  -i          : inverts the output so the first character will change very often
 
  -l          : literal characters to use in -t @,%^
  
  -o          : allows you to specify the file to write the output to, eg:
                wordlist.txt
  
  -p          : prints permutations without repeating characters.  This option
                CANNOT be used with -s.  It also ignores min and max lengths.
  
  -q          : Like the -p option except it reads the strings from the specified
                file.  It CANNOT be used with -s.  It also ignores min and max.
  
  -r          : resume a previous session.  You must use the same command line as
                the previous session.
  
  -s          : allows you to specify the starting string, eg: 03god22fs
  
  -t [FIXED]@,%^  : allows you to specify a pattern, eg: @@god@@@@
                where the only the @'s will change with lowercase letters
                the ,'s will change with uppercase letters
                the %'s will change with numbers
                the ^'s will change with symbols
  
  -u          : The -u option disables the printpercentage thread.  This should be the last option.
 
  -z          : adds support to compress the generated output.  Must be used
                with -o option.  Only supports gzip, bzip, lzma, and 7z.

## Installation

Compiles on:
     linux (32 and 64 bit Ubuntu for sure, 32 and 64 bit Linux in
     general works.  I have received word that crunch compiles on MacOS.
     Juan reports Freebsd x64, i386 and OSX Mountain Lion compiles and works
     perfectly. It should compile on the other Unix and Linux OSs but I don't
     don't have access to any of the those systems.  Please let me know.

## License

https://sourceforge.net/projects/crunch-wordlist/

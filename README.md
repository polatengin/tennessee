# `polatengin` man page

I was using `man` pages to learn more about `git rev-list` _(they really helped me understand how to use it)_.

Then I realized, as `polatengin`, I don't have a `man` page for myself 🤷‍♂️.

I asked myself, "Why not?"

> `man` pages are a great way to document tools and make them easier to understand.

So, I decided to create one for `polatengin`. My goal is to learn how to create and share a `man` page.

## `man` pages

`man` pages are the manual pages for commands in Unix-like operating systems. They provide detailed information about commands, their options, and usage.

## `man man` command

Let's start with the `man` command itself. You can use the `man` command to view the manual pages of other commands, including the `man` command itself.

```bash
man man
```

![man man command screenshot](https://github.com/user-attachments/assets/d9d1d382-81b4-4724-afe9-176b39da27c3)

There is a section in the `man` page of the `man` command that explains the sections of the manual pages. Here is a summary of the sections:

| Section | Description |
|---------|-------------|
| 1 | Executable programs or shell commands |
| 2 | System calls (functions provided by the kernel) |
| 3 | Library calls (functions within program libraries) |
| 4 | Special files (usually found in /dev) |
| 5 | File formats and conventions, e.g. /etc/passwd |
| 6 | Games |
| 7 | Miscellaneous (including macro packages and conventions), e.g. man(7), groff(7) |
| 8 | System administration commands (usually only for root) |
| 9 | Kernel routines [Non standard] |

For my `polatengin` `man` page, I will use section _7_, which is for _miscellaneous (including macro packages and conventions)_.

In the _Overview_ section of the output of the `man man` command, you can see that the man pages are stored in the `nroff` format. This is a text formatting program that is used to format the manual pages.

> Manual pages are normally stored in nroff(1) format under a directory such as /usr/share/man. In some installations, there may also be preformatted cat pages to improve performance. See manpath(5) for details of where these files are stored.

Also in the _Overview_ section, you can see that the `man` pages are stored in the `manpath`, which can be find using the `manpath` command.

```bash
manpath

/usr/local/share/nvm/versions/node/v22.15.0/share/man:/usr/local/man:/usr/local/share/man:/usr/share/man
```

## `nroff` format

The `nroff` format is a text formatting program that is used to format the manual pages. It is a simple text format that can be easily read and edited.

```bash
man nroff
```

`nroff` format uses `roff` language, which is a macro language for formatting text.

We can find details about the `roff` language in the `Miscellaneous` category of the man page of `man`.

```bash
man 7 man
```

![man 7 man command screenshot](https://github.com/user-attachments/assets/961e675c-594b-49fe-bda9-46d7767b3013)

## Sample formats

| Format | Description |
|--------|-------------|
| .TH | Title header |
| .SH | Section header |
| .B | Bold text |
| .I | Italic text |
| .BI | Bold and italic text |
| .PP | Paragraph break |

## Creating a `man` page for `polatengin`

To create a `man` page for `polatengin`, we will create a file named `polatengin.7`, which is the standard naming convention for `man` pages in section 7.

```bash
vim polatengin.7
```


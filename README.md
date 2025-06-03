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

Open a terminal panel in the editor and check the format macros in the `man` page of `man`.

```bash
:terminal

man 7 man
```

Now, we can start writing our `man` page using the `nroff` format.

```nroff
.TH EnginPolat 7

.SH NAME

Hello 👋, this is Engin Polat

.SH REFERENCES

GitHub \- https://github.com/polatengin

LinkedIn \- https://www.linkedin.com/in/polatengin

.SH DESCRIPTION

My name is Engin Polat (pronouns, he/him 🙋‍♂️), I'm based in Seattle area, beautiful city Sammamish 🌅

I'm a versatile Software Engineer with over 20 years of comprehensive experience, focused on working with challenging projects and learning while working.

I'm currently working at my dream job as a Senior Software Engineer in Microsoft. I actively contribute to projects that make cloud development smoother for everyone.

Why do I work for Microsoft

I work for Microsoft because it is a great place to work where I can use my skills and talents to make a difference. Microsoft offers excellent job satisfaction, a chance to work on cutting-edge technology, and a chance to make a real difference in the world.

I enjoy working on projects that are important to the company and that have a real impact on the world. I feel that my work is meaningful and that I am making a contribution to the company.

I like the constantly learning new things and working on new projects.

Microsoft is also a great place to work because of the people. The people at Microsoft are some of the smartest, most talented, and most driven people I have ever met. I feel fortunate to be able to work with such talented and passionate people.

What is my job in Microsoft
I'm working with the biggest enterprises and communities all around the world, trying to solve their most sophisticated problems with scalable and future-proof solutions 👍
```

## Compiling the `man` page

To compile the `man` page, we just use the `gzip` command to compress the `polatengin.7` file into a `polatengin.7.gz` file.

```bash
gzip polatengin.7
```

After running the command, you will see the `polatengin.7` file is replaced with the new file named `polatengin.7.gz`.

## Viewing the content of the gzipped `man` page

To view the content of the gzipped `man` page, we can use the `zcat` command.

```bash
zcat polatengin.7.gz
```

This will display the content of the `polatengin.7` file in the terminal.

## Installing the `man` page

To install the `man` page, we need to copy the `polatengin.7.gz` file to the appropriate directory in the `manpath`.

```bash
manpath

/usr/local/share/nvm/versions/node/v22.15.0/share/man:/usr/local/man:/usr/local/share/man:/usr/share/man
```

Let's check the `/usr/share/man` directory to see it's content.

```bash
ls -lah /usr/share/man

drwxr-xr-x 1 root root 16384 Jun  3 17:20 man1
drwxr-xr-x 2 root root 20480 Apr  9 05:56 man2
drwxr-xr-x 1 root root 12288 Apr  9 05:56 man3
drwxr-xr-x 2 root root  4096 Apr  9 05:56 man4
drwxr-xr-x 1 root root  4096 Jun  3 17:18 man5
drwxr-xr-x 2 root root  4096 Apr  9 05:56 man6
drwxr-xr-x 1 root root  4096 Jun  3 17:18 man7
drwxr-xr-x 1 root root  4096 Jun  3 17:18 man8
```

> If the `man7` directory does not exist, you can create it using the following command:
>
> ```bash
> sudo mkdir /usr/share/man/man7
> ```

Each directory corresponds to a category in the `man` pages. Since we are creating a `man` page for section 7, we will copy the `polatengin.7.gz` file to the `man7` directory.

```bash
sudo cp polatengin.7.gz /usr/share/man/man7
```


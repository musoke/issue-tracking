<h1 align="center">
  <br>
  <a href="http://sit.fyi"><img src="https://raw.githubusercontent.com/sit-fyi/sit/master/logo.png" alt="Markdownify" width="150"></a>
  <br>
  <br>
  SIT Issue Tracking
  <br>
</h1>

<h4 align="center">Serverless issue tracker for decentralized teams</h4>

<p align="center">
 <a href="https://github.com/sit-fyi/issue-tracking/releases"><img alt="Release" src="https://img.shields.io/github/release/sit-fyi/issue-tracking.svg"></a>
 <a href="https://gitter.im/sit-fyi/Lobby"><img alt="Chat" src="https://badges.gitter.im/sit-fyi/Lobby.png"></a>
</p>

<p align="center">
  [
    <a href="https://github.com/sit-fyi/issue-tracking/releases"><b>Download</b></a> |
    <a href="web/documentation/getting_started.md"><b>Getting Started</b></a> |
    <a href="#questions-bug-reports-etc"><b>Issues & Merge Requests</b></a>
  ]
</p>

SIT Issue Tracking is a compact tool to track and share project issues in and between
decentralized teams. Its goal is to lower the barrier for having an independently
operated, shared issue tracker. Instead of having to setup and maintain a server
and a database, or having to rely on services of an external third party, SIT can
be initialized with it and started as simply as this:

```
$ sit init
# copy or link `issue-tracking` module to `.sit/modules/issue-tracking`
$ sit-web
```

That's it. Now you can check out the [Getting Started](web/documentation/getting_started.md) guide.

<center>
<p align="center">
<img src="web/documentation/webui_example.png">
<small><i>(An example of running sit-web)</i></small>
</p>
</center>

### How to Copy or Link `issue-tracking` Module

If you are using a Git repository and don't want to carry the entire contents of this repository, simply
using `git submodules` is a great way to accomplish this:

```
git submodule add https://github.com/sit-fyi/issue-tracking .sit/modules/issue-tracking
```

This allows to pin a specific version of `issue-tracking` and update it when neccessary.

When *not* using a Git repository, or if it is preferrable to carry all the modules within your SIT
repository (for example, if you don't want to depend on the availability of the module in the future),
you can simply copy the entire module into `.sit/modules/issue-tracking`:

```
git clone --depth=1 https://github.com/sit-fyi/issue-tracking .sit/modules/issue-tracking
rm -rf .sit/modules/issue-tracking/.sit .sit/modules/issue-tracking/.git
```

## Why Should I Care?

As far as analogies go, we're doing to issue tracking what Git did to version control systems. But let us
further elaborate on a few benefits to consider:

* **Works offline**. You can synchronize the issues, go offline and work
  on them without needing a connection. You can synchronize at any time later.
* **Contextualizes state**. When used together with an SCM (such as Git), you can see the
  state and status of any issue at any given revision (*"what release branches is this
  closed on?"*)
* **Continuously localizes data**. You can access the data at any time. No API rate limits. It's on your filesystem.
* **Adapts to your team topology**. Synchronization can be done over Git, Dropbox, Keybase,
  USB flash drives or anything else that allows you to copy files between computers.
* **Malleable**. You can make it handle workflows and payloads original authors never anticipated. The customization
  is in its blood.

## Project Status

It is in the early adopter stage. It's usable but not everything is done yet and
some things will change. We're publishing releases regularly but always encourage
trying out the latest and greatest master branch.

## Obtaining SIT

All our releases are hosted on [GitHub](https://github.com/sit-fyi/sit/releases)
and binary files can be downloaded from there.

## Build Instructions

As SIT is currently in its early days, sometimes it might make sense to use a pre-release build. We encourage that. It helps us building a better product.

Firstly, you will need to install Rust 1.24.1. Luckily
it is typically a very simple process. You can find
instructions on [Rust's website](https://www.rust-lang.org/en-US/install.html).

Now, after that has been taken care of, time to check
out SIT and build it:

```
git clone https://github.com/sit-fyi/sit
cd sit
cargo build --release
```

Now, you can copy `target/release/sit` and `target/release/sit-web` to your
`PATH` or add `/path/to/target/release` to `PATH` to always have the most
recent version available.

## Questions, Bug Reports, etc.?

This project is using SIT for tracking issues (duh!) and because of this, GitHub
issues are turned off. It's a good excuse to try out SIT if you have an
issue to file!

You will get all issue updates when you fetch this git repository. All updates
will come through it as well.

Simply run `sit-web` in this repository's clone and open it in the browser.

#### Send Updates to Upstream

Once you've used `sit web` or `script mr` to work on the issues,
you can send the updates to this repository:

1. Create a branch (as a convention, you can use your issue ID or an added record ID as a branch name, but free to choose anything else, preferrably unique)
2. Add new files in `.sit` and commit them. Commit message can be simply "Added issue <ISSUE-ID>"
   or, say, "Commented on issue <ISSUE-ID>"
3. Send it out to the Inbox: `git send-email --to=issue-tracking@inbox.sit.fyi master..<branch>`
4. If the commit only contains new records (nothing else is permitted!) the Inbox
   will accept the push and immediately forward it to sit's master repository on GitHub.
   Otherwise, the push will be rejected.

### Preparing a merge request

Please refer to [CONTRIBUTING](https://github.com/sit-fyi/issue-tracking/blob/master/CONTRIBUTING.md#preparing-a-merge-request) for the instruction.

## License

SIT and this module are distributed under the terms of both the MIT license and the Apache License (Version 2.0).

See LICENSE-APACHE and LICENSE-MIT for details.

## Contributing

This project is in its very early days and we will always be welcoming
contributors.

Our goal is to encourage frictionless contributions to the project. In order to
achieve that, we use Unprotocols' [C4 process](https://rfc.unprotocols.org/spec:1/C4)
as an inspiration. Please read it, it will answer a lot of questions. Our goal is to
merge patches as quickly as possible and make new stable releases regularly.

In a nutshell, this means:

* We merge patches rapidly (try!)
* We are open to diverse ideas
* We prefer code now over consensus later

To learn more, read our [contribution guidelines](CONTRIBUTING.md)

-   [General throat clearing](#general-throat-clearing)
-   [How do we build code?](#how-do-we-build-code)
-   [Project Planning](#project-planning)
    -   [Project checklist](#project-checklist)
    -   [Herding your cats](#herding-your-cats)
    -   [Scheduling](#scheduling)
-   [Documentation](#documentation)
    -   [Documentation should describe what you actually
        do](#documentation-should-describe-what-you-actually-do)
    -   [Documentation workflow](#documentation-workflow)
-   [Development workflow](#development-workflow)
    -   [Your goal: Repeatable
        workflows](#your-goal-repeatable-workflows)
    -   [Issue Tracking](#issue-tracking)
    -   [An aside about
        \"methodologies\"](#an-aside-about-methodologies)
    -   [An aside about boiling the
        ocean](#an-aside-about-boiling-the-ocean)
    -   [Testing and Validation](#testing-and-validation)
    -   [Version Control](#version-control)
-   [Data and file management](#data-and-file-management)
    -   [Your goal: Maintain the integrity of your distributed file
        system](#your-goal-maintain-the-integrity-of-your-distributed-file-system)
    -   [Project File Structure](#project-file-structure)
    -   [Naming Things](#naming-things)
    -   [Data Formats](#data-formats)
    -   [Backups](#backups)
-   [Tooling](#tooling)
    -   [Publishing and markup
        languages](#publishing-and-markup-languages)
    -   [Choosing a language is choosing an
        ecosystem](#choosing-a-language-is-choosing-an-ecosystem)
    -   [Code Editors](#code-editors)
    -   [Helpful Tools](#helpful-tools)
-   [It\'s made of people](#its-made-of-people)
-   [Coda: The cloud is just someone else\'s
    computer](#coda-the-cloud-is-just-someone-elses-computer)

# General throat clearing

1.  This is a highly opinionated talk.
2.  Experienced software developers can rant for hours about the things
    you **must** do or **must not** do, but the list of things that you
    must or must not do is actually quite short (e.g., you must make
    backups. No one disputes this).
3.  However, there are many activities for which you should have a
    process. The exact process doesn\'t matter, what matters is that you
    **have** a process and it works for you.
4.  The purpose of this talk is to help you think through your workflow
    and options, and come up with a process that works for you. We have
    opinions (see 1), but these opinions are based on our experiences
    building processes for our individual circumstances.

# How do we build code?

1.  Work from the inside out. Increase the complexity and generality of
    your code as circumstances demand.
2.  Given (1), commit to rewriting your code on an ongoing basis.
3.  Use code organization (functions, objects, modules, etc.) to reduce
    cognitive overhead
    1.  Compartmentalizing your code makes it easier to navigate and
        understand
    2.  Code chunks that are truly done can be \"frozen\" as
        compartmentalized functions or modules, making it easier to
        reason about and rewrite the remaining code
4.  Preserve useful practices across projects by developing a standard
    approach and toolkit

# Project Planning

## Project checklist

1.  What are the deliverables? Code, analyses, figures, white papers,
    journal publications, etc.
2.  What is the time scale for the deliverables?
3.  Who are the responsible parties for each of the deliverables?
4.  What are the dependencies? For example: Data analysis requires data
    cleanup and validation, writing code, testing code
5.  What are the **implied** dependencies?
    1.  Documentation
    2.  Testing
    3.  Backups
    4.  System administration (installation, upgrades, there\'s only one
        person who knows how to troubleshoot network errors, etc.)
    5.  Training

## Herding your cats

1.  By default, give everyone access to everything
2.  Establish a common workflow for collaborating on code (e.g., \"we
    share all code in a private Github repository\")
3.  Establish a common workflow for collaborating on documents
4.  Large group? Delegate to team leads.

## Scheduling

A common conversation on development teams:

Q: \"How long will X take?\"

A: \"Four weeks\"

X is irrelevant. From this we learn that there are two kinds of
schedules:

1.  Evidence-based schedules
2.  Lies

### Evidence-based scheduling

cf.
<https://www.joelonsoftware.com/2007/10/26/evidence-based-scheduling/>

1.  Estimate task time
2.  Start the clock
3.  Complete the task
4.  Stop the clock
5.  Assess accuracy
6.  Weight new estimates

### Some comments on evidence-based scheduling

1.  You can estimate the task time using time or \"points\" (i.e. the
    relative size of tasks)
2.  Note the missing step: You don\'t stop the clock when you go
    off-task in (3). This is deliberate; your inability to predict
    interruptions is one of the major sources of estimation error.
3.  You can assess the accuracy of your schedule estimates by eyeball or
    by using regression, depending on your commitment to the bit.

# Documentation

## Documentation should describe what you actually do

Contextualize all the things!

1.  Why did you make this decision?
2.  How does this work?

## Documentation workflow

You want an easy-to-use collaborative workflow. Here are some options
(not mutually exclusive):

1.  Explanatory code comments
2.  README files (Github will render Markdown README files as nice web
    pages)
3.  Github wiki
4.  Many other wikis
5.  Word documents in Dropbox, I guess? Sometimes you have to make
    compromises.

# Development workflow

## Your goal: Repeatable workflows

Can future you...

1.  Recreate your files?
2.  Distinguish between raw and processed data?
3.  Recreate your analyses?
4.  Understand your code?
5.  Prove your code is correct?
6.  Guarantee you haven't pasted a six-month-old, stale analysis into
    your final draft?

## Issue Tracking

### Key features

1.  Issue title
2.  Issue description
3.  Issue creator
4.  Current assignee
5.  Status
6.  Dates (created, resolved, closed, re-opened)
7.  Comments
8.  Topic tags, version tags, etc
9.  Version control integration (\"fixed by commit X\"; this is a
    nice-to-have but not necessary feature)
10. Support for searching, filtering, and sorting

### Options

1.  Free
    -   Github project issues
2.  Free-ish
    -   Trello
    -   Microsoft Planner
3.  Paid (sometimes fiddly)
    -   Airtable
    -   Jira
    -   Many many others
4.  Locally-hosted (fiddly)
    -   Fossil
    -   Trac

## An aside about \"methodologies\"

There are many \"methodologies\" (Kanban, Agile, etc.). Just ignore
them.

You have a pile of work.

1.  Try to organize the work in to bite-size chunks
2.  Try to keep track of who's doing what
3.  Try to do the important stuff first

## An aside about boiling the ocean

Start small and build the code in a way that scales. Don\'t jump to the
next level of complexity until you need it.

1.  <https://adamdrake.com/command-line-tools-can-be-235x-faster-than-your-hadoop-cluster.html>
2.  <https://livefreeordichotomize.com/2019/06/04/using_awk_and_r_to_parse_25tb/>

## Testing and Validation

How do you know your code does what you say it does? A taxonomy of
testing strategies, from simple to complex:

1.  Defensive coding
    1.  Assume your inputs are bad, and include tests of input
        correctness in your code.
    2.  Use `assert` statements (sparingly) for things that should never
        break.
2.  Unit tests: Generally overkill (not enough return for time
    invested). Use selectively in places where the code tends to change
    a lot.
3.  Integration testing: The sweet spot for small-to-medium projects.
    For example:
    1.  Start with a vetted sample input file
    2.  Generate intermediate data and compare to known intermediate
        data
    3.  Run analyses and compare results to known results
    4.  Write results to output and compare with known output file (this
        is different than 3!)

## Version Control

Oh god I broke it.

### The exhortation

1.  No one wants to eat their vegetables
2.  If you don\'t eat your vegetables you\'ll die
3.  Eat your vegetables

### Version control in practice

1.  One branch should always be deliverable, working code. Typically
    this is \"main\".
2.  New work happens on development branches.
3.  Merge new work using a \"general and lieutenants\" workflow:
    1.  Developer (\"lieutenant\") pushes development branch to shared
        repository
    2.  Project lead (\"general\") merges development branch into main
        branch, or talks to developer if there\'s a conflict
4.  There are many possible workflows; the more your team knows, the
    more options you have.

# Data and file management

## Your goal: Maintain the integrity of your distributed file system

Q: \"What if everything was distributed?\"

A: \"Everything **is** distributed.\"

Every research group has an M to N to O mapping of Researchers to
Machines to Files. The goal is to maintain the integrity of that
many-to-many-to-many mapping.

## Project File Structure

![](files/project_structure.svg)

cf. <https://doi.org/10.1371/journal.pcbi.1000424> via
<https://github.com/leonjessen/talks>

A nice feature of this kind of directory structure is that it lends
itself to automation.

## Naming Things

\"The two hardest problems in computer science are cache invalidation,
naming things, and off-by-one errors.\"

-   <https://twitter.com/secretGeek/status/7269997868>

### Basics of naming

\<meaningful name\> . \<file extension\>

1.  Use meaningful names, with some kind of systematic convention. An
    example of embedding metadata in the name is the BIDS file naming
    format: <https://github.com/bids-standard>
2.  Prefer underscores to hyphens, never use spaces
3.  For software, use either Semantic versioning or Calendar versioning.
4.  For data files, results, and documents, you probably want Calendar
    versioning. Your scripts can automatically name things!

### Semantic versioning

\<major version\> . \<minor version\> . \<bugfix version\> . \<file
extension\>

"project_author_2.7.4.txt"

"study_condition_4.2.11.out"

### Calendar versioning

\<meaningful name\> . \<ISO date\> . \<increment\> . \<file extension\>

"project_author_20190327.3.txt"

"study_condition_20181105.5.out"

## Data Formats

1.  Use a sensible representation and follow standards where they exist.
    Examples of sensible representations:
    1.  Tabular: Excel, CSV, TSV
    2.  Tree-structured data interchange: XML, JSON, RDF
    3.  Tabular with complex relations: Relational database (SQLite,
        PostgreSQL)
2.  Prefer \"open\" data formats. This means:
    1.  unencumbered by patents or royalties
    2.  interoperable with common tools

## Backups

"There are two kinds of people: Those who make backups, and those who
will make backups."

-   Gregory A. Miller

# Tooling

The real open source mantra should be: "Information wants to be
exchangeable." You should view all of your tools as components of a
loosely-coupled workflow.

## Publishing and markup languages

### Simplified markup

1.  Markdown (Github and many other places)
2.  reStructured Text (Python and Sphinx documentation)
3.  Org-mode (Emacs)

### Complex markup

1.  Latex (document publishing)
2.  HTML (web and ebook publishing)

## Choosing a language is choosing an ecosystem

![](files/language_ecosystem.svg)

### Language features

A language (and some of its libraries) is maintained by a core team, and
has a sales pitch about what makes it neat in theory. However, the core
language features are not enough; there are additional practical
considerations:

1.  **Community**. This can include forums, documentation, Q&A sites,
    and other evidence of enthusiastic hobby and personal use. It\'s
    easy to find help on how to get started. There is evidence of
    continuing organic support for the language ecosystem.
2.  **Tools**. Features that make the language usable in day-to-day
    work, including: Code editor support, syntax highlighting,
    debuggers, profiling, tools for packaging and deployment, version
    control, testing, automated doc extraction, and integration with
    outside tools (web servers, databases, interchange formats like
    XML/JSON). Some of this will be included in Core Libraries.
3.  **Working deployments**. You see the language being used in
    real-world projects. The pitfalls for deployment, performance, and
    scaling are well-known and documented. The community has confidence
    in (mostly) bug-free operation. Edge cases, errata, and know bugs
    are documented. There is a community of understanding around how to
    use the tool effectively and avoid tarpits.

### When is a language ready?

![](files/programmer_migration.svg)

-   <https://apenwarr.ca/log/20190318>

In general, a language ecosystem will do some things well and other
things poorly. Some examples:

1.  Julia: Good tools and community, but we don't see it widely deployed
2.  Rust: Checks all boxes, but don't have a lot of deployed examples
    for scientific computing **specifically**. Example of a promising
    ecosystem.
3.  Many proprietary statistics tools: Little to no organic support for
    integrating into a wider toolchain, which can be problematic from a
    purely practical standpoint.

## Code Editors

The short version: There are many editors, and everyone should try to
find one that suits them.

cf.
<https://github.com/elliewix/Ways-Of-Installing-Python/blob/master/ways-of-installing.md#the-grand-trio-of-tools>

## Helpful Tools

Lots of little tools that are complimentary to your main toolchain.
Examples include: shell (bash), pandoc, graphviz/dot, SQL, tree, stow,
awk, sed...

# It\'s made of people

We also never taught you how to manage a team. Whoops! Here are some
books?

1.  Peopleware: Productive Projects and Teams (DeMarco & Lister)

    One of the few project management books that doesn\'t suck.
    Specifically about managing software projects, but contains a lot of
    generally useful guidance.

2.  The Mythical Man-Month (Brooks)

    This has all happened before; this will all happen again. Fred
    Brooks tells stories of software projects gone bad.

3.  Getting to Yes: Negotiating Agreement Without Giving In (Fisher &
    Ury)

    You can\'t just give people orders all the time.

4.  The Workflow of Data Analysis Using Stata (Long)

    Lots of generic advice about data management.

# Coda: The cloud is just someone else\'s computer

Someone\'s slow, expensive computer

-   <https://news.ycombinator.com/item?id=23314973>

| AWS                   | Free or DIY                 |
|-----------------------|-----------------------------|
| Route 53              | NSD                         |
| WAF                   | modsecurity                 |
| SES                   | Postfix                     |
| Inspector             | OSSEC                       |
| GuardDuty             | Snort                       |
| Data Pipeline         | cron and bash               |
| Athena                | Prestodb                    |
| Glue                  | Hive Metastore and Spark    |
| OpsWorks              | Chef                        |
| VPC                   | a VLAN                      |
| Snowball              | a truck full of hard drives |
| CloudWatch            | syslogd                     |
| Neptune               | Neo4j                       |
| ElastiCache           | Redis                       |
| DynamoDB              | MongoDB                     |
| S3 Glacier            | DVD backup                  |
| EFS                   | NFS                         |
| Elastic Block Store   | a SAN                       |
| Elastic Beanstalk     | Apache Tomcat               |
| EMR                   | Apache Hadoop               |
| Elastic Cloud Compute | a virtual machine           |
| Kinesis               | Apache Kafka                |
| QuickSight            | Tableau                     |


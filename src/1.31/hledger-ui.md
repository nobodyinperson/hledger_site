<!-- Generated by "Shake webmanuals" from hledger-ui/hledger-ui.m4.md doc/common.m4 hledger/Hledger/Cli/Commands/commands.m4 hledger-ui/.version.m4 hledger-ui/.date.m4 -->
<div class="docversions"></div>

# hledger-ui

<div class="pagetoc manual">

<!-- toc -->
</div>

## NAME

hledger-ui - robust, friendly plain text accounting (TUI version)

## SYNOPSIS

`hledger-ui    [OPTS] [QUERYARGS]`\
`hledger ui -- [OPTS] [QUERYARGS]`

## DESCRIPTION

This manual is for hledger\'s terminal interface, version 1.31. See also
the hledger manual for common concepts and file formats.

hledger is a robust, user-friendly, cross-platform set of programs for
tracking money, time, or any other commodity, using double-entry
accounting and a simple, editable file format. hledger is inspired by
and largely compatible with ledger(1), and largely interconvertible with
beancount(1).

<div class="screenshots-right">

<a href="/images/hledger-ui/hledger-ui-sample-acc2.png" class="highslide" onclick="return hs.expand(this)"><img src="/images/hledger-ui/hledger-ui-sample-acc2.png" title="Accounts screen with query and depth limit" height="180"/></a>
<a href="/images/hledger-ui/hledger-ui-sample-acc.png" class="highslide" onclick="return hs.expand(this)"><img src="/images/hledger-ui/hledger-ui-sample-acc.png" title="Accounts screen" height="180"/></a>
<a href="/images/hledger-ui/hledger-ui-sample-acc-greenterm.png" class="highslide" onclick="return hs.expand(this)"><img src="/images/hledger-ui/hledger-ui-sample-acc-greenterm.png" title="Accounts screen with greenterm theme" height="180"/></a>
<a href="/images/hledger-ui/hledger-ui-sample-txn.png" class="highslide" onclick="return hs.expand(this)"><img src="/images/hledger-ui/hledger-ui-sample-txn.png" title="Transaction screen" height="180"/></a>
<a href="/images/hledger-ui/hledger-ui-sample-reg.png" class="highslide" onclick="return hs.expand(this)"><img src="/images/hledger-ui/hledger-ui-sample-reg.png" title="Register screen" height="180"/></a>
<a href="/images/hledger-ui/hledger-ui-bcexample-acc.png" class="highslide" onclick="return hs.expand(this)"><img src="/images/hledger-ui/hledger-ui-bcexample-acc.png" title="beancount example accounts" height="180"/></a>
<a href="/images/hledger-ui/hledger-ui-bcexample-acc-etrade-cash.png" class="highslide" onclick="return hs.expand(this)"><img src="/images/hledger-ui/hledger-ui-bcexample-acc-etrade-cash.png" title="beancount example's etrade cash subaccount" height="180"/></a>
<a href="/images/hledger-ui/hledger-ui-bcexample-acc-etrade.png" class="highslide" onclick="return hs.expand(this)"><img src="/images/hledger-ui/hledger-ui-bcexample-acc-etrade.png" title="beancount example's etrade investments, all commoditiess" height="180"/></a>

</div>

hledger-ui is hledger\'s terminal interface, providing an efficient
full-window text UI for viewing accounts and transactions, and some
limited data entry capability. It is easier than hledger\'s command-line
interface, and sometimes quicker and more convenient than the web
interface.

Like hledger, it reads from (and appends to) a journal file specified by
the `LEDGER_FILE` environment variable (defaulting to
`$HOME/.hledger.journal`); or you can specify files with `-f` options.
It can also read timeclock files, timedot files, or any CSV/SSV/TSV file
with a date field. (See hledger(1) -\> Input for details.)

Unlike hledger, hledger-ui hides all future-dated transactions by
default. They can be revealed, along with any rule-generated periodic
transactions, by pressing the F key (or starting with \--forecast) to
enable \"forecast mode\".

## OPTIONS

Any QUERYARGS are interpreted as a hledger search query which filters
the data.

hledger-ui provides the following options:

`-w --watch`
:   watch for data and date changes and reload automatically

`--theme=default|terminal|greenterm`
:   use this custom display theme

`--menu`
:   start in the menu screen

`--cash`
:   start in the cash accounts screen

`--bs`
:   start in the balance sheet accounts screen

`--is`
:   start in the income statement accounts screen

`--all`
:   start in the all accounts screen

`--register=ACCTREGEX`
:   start in the (first) matched account\'s register screen

`--change`
:   show period balances (changes) at startup instead of historical
    balances

`-l --flat`
:   show accounts as a flat list (default)

`-t --tree`
:   show accounts as a tree

hledger-ui also supports many of hledger\'s general options (and the
hledger manual\'s command line tips also apply here):

### General help options

`-h --help`
:   show general or COMMAND help

`--man`
:   show general or COMMAND user manual with man

`--info`
:   show general or COMMAND user manual with info

`--version`
:   show general or ADDONCMD version

`--debug[=N]`
:   show debug output (levels 1-9, default: 1)

### General input options

`-f FILE --file=FILE`
:   use a different input file. For stdin, use - (default:
    `$LEDGER_FILE` or `$HOME/.hledger.journal`)

`--rules-file=RULESFILE`
:   Conversion rules file to use when reading CSV (default: FILE.rules)

`--separator=CHAR`
:   Field separator to expect when reading CSV (default: \',\')

`--alias=OLD=NEW`
:   rename accounts named OLD to NEW

`--anon`
:   anonymize accounts and payees

`--pivot FIELDNAME`
:   use some other field or tag for the account name

`-I --ignore-assertions`
:   disable balance assertion checks (note: does not disable balance
    assignments)

`-s --strict`
:   do extra error checking (check that all posted accounts are
    declared)

### General reporting options

`-b --begin=DATE`
:   include postings/txns on or after this date (will be adjusted to
    preceding subperiod start when using a report interval)

`-e --end=DATE`
:   include postings/txns before this date (will be adjusted to
    following subperiod end when using a report interval)

`-D --daily`
:   multiperiod/multicolumn report by day

`-W --weekly`
:   multiperiod/multicolumn report by week

`-M --monthly`
:   multiperiod/multicolumn report by month

`-Q --quarterly`
:   multiperiod/multicolumn report by quarter

`-Y --yearly`
:   multiperiod/multicolumn report by year

`-p --period=PERIODEXP`
:   set start date, end date, and/or reporting interval all at once
    using [period expressions](hledger.html#period-expressions) syntax

`--date2`
:   match the secondary date instead (see command help for other
    effects)

`--today=DATE`
:   override today\'s date (affects relative smart dates, for
    tests/examples)

`-U --unmarked`
:   include only unmarked postings/txns (can combine with -P or -C)

`-P --pending`
:   include only pending postings/txns

`-C --cleared`
:   include only cleared postings/txns

`-R --real`
:   include only non-virtual postings

`-NUM --depth=NUM`
:   hide/aggregate accounts or postings more than NUM levels deep

`-E --empty`
:   show items with zero amount, normally hidden (and vice-versa in
    hledger-ui/hledger-web)

`-B --cost`
:   convert amounts to their cost/selling amount at transaction time

`-V --market`
:   convert amounts to their market value in default valuation
    commodities

`-X --exchange=COMM`
:   convert amounts to their market value in commodity COMM

`--value`
:   convert amounts to cost or market value, more flexibly than -B/-V/-X

`--infer-equity`
:   infer conversion equity postings from costs

`--infer-costs`
:   infer costs from conversion equity postings

`--infer-market-prices`
:   use costs as additional market prices, as if they were P directives

`--forecast`
:   generate transactions from [periodic
    rules](hledger.html#periodic-transactions),
:   between the latest recorded txn and 6 months from today,
:   or during the specified PERIOD (= is required).
:   Auto posting rules will be applied to these transactions as well.
:   Also, in hledger-ui make future-dated transactions visible.

`--auto`
:   generate extra postings by applying [auto posting
    rules](hledger.html#auto-postings) to all txns (not just forecast
    txns)

`--verbose-tags`
:   add visible tags indicating transactions or postings which have been
    generated/modified

`--commodity-style`
:   Override the commodity style in the output for the specified
    commodity. For example \'EUR1.000,00\'.

`--color=WHEN (or --colour=WHEN)`
:   Should color-supporting commands use ANSI color codes in text
    output.
:   \'auto\' (default): whenever stdout seems to be a color-supporting
    terminal.
:   \'always\' or \'yes\': always, useful eg when piping output into
    \'less -R\'.
:   \'never\' or \'no\': never.
:   A NO_COLOR environment variable overrides this.

`--pretty[=WHEN]`
:   Show prettier output, e.g. using unicode box-drawing characters.
:   Accepts \'yes\' (the default) or \'no\' (\'y\', \'n\', \'always\',
    \'never\' also work).
:   If you provide an argument you must use \'=\', e.g.
    \'\--pretty=yes\'.

When a reporting option appears more than once in the command line, the
last one takes precedence.

Some reporting options can also be written as [query
arguments](hledger.html#queries).

## MOUSE

In most modern terminals, you can navigate through the screens with a
mouse or touchpad:

-   Use mouse wheel or trackpad to scroll up and down
-   Click on list items to go deeper
-   Click on the left margin (column 0) to go back.

## KEYS

Keyboard gives more control.

`?` shows a help dialog listing all keys. (Some of these also appear in
the quick help at the bottom of each screen.) Press `?` again (or
`ESCAPE`, or `LEFT`, or `q`) to close it. The following keys work on
most screens:

The cursor keys navigate: `RIGHT` or `ENTER` goes deeper, `LEFT` returns
to the previous screen, `UP`/`DOWN`/`PGUP`/`PGDN`/`HOME`/`END` move up
and down through lists. Emacs-style
(`CTRL-p`/`CTRL-n`/`CTRL-f`/`CTRL-b`) and VI-style (`k`,`j`,`l`,`h`)
movement keys are also supported. A tip: movement speed is limited by
your keyboard repeat rate, to move faster you may want to adjust it. (If
you\'re on a mac, the karabiner app is one way to do that.)

With shift pressed, the cursor keys adjust the report period, limiting
the transactions to be shown (by default, all are shown).
`SHIFT-DOWN/UP` steps downward and upward through these standard report
period durations: year, quarter, month, week, day. Then,
`SHIFT-LEFT/RIGHT` moves to the previous/next period. `T` sets the
report period to today. With the `-w/--watch` option, when viewing a
\"current\" period (the current day, week, month, quarter, or year), the
period will move automatically to track the current date. To set a
non-standard period, you can use `/` and a `date:` query.

(Mac users: SHIFT-DOWN/UP keys do not work by default in Terminal, as of
MacOS Monterey. You can configure them as follows: open Terminal, press
CMD-comma to open preferences, click Profiles, select your current
terminal profile on the left, click Keyboard on the right, click + and
add this for Shift-Down: `\033[1;2B`, click + and add this for Shift-Up:
`\033[1;2A`. Press the Escape key to enter the `\033` part, you can\'t
type it directly.)

`/` lets you set a general filter query limiting the data shown, using
the same [query terms](hledger.html#queries) as in hledger and
hledger-web. While editing the query, you can use [CTRL-a/e/d/k, BS,
cursor
keys](http://hackage.haskell.org/package/brick-0.7/docs/brick-widgets-edit.html#t:editor);
press `ENTER` to set it, or `ESCAPE`to cancel. There are also keys for
quickly adjusting some common filters like account depth and transaction
status (see below). `BACKSPACE` or `DELETE` removes all filters, showing
all transactions.

As mentioned above, by default hledger-ui hides future transactions -
both ordinary transactions recorded in the journal, and periodic
transactions generated by rule. `F` toggles forecast mode, in which
future/forecasted transactions are shown.

`ESCAPE` resets the UI state and jumps back to the top screen, restoring
the app\'s initial state at startup. Or, it cancels minibuffer data
entry or the help dialog.

`CTRL-l` redraws the screen and centers the selection if possible
(selections near the top won\'t be centered, since we don\'t scroll
above the top).

`g` reloads from the data file(s) and updates the current screen and any
previous screens. (With large files, this could cause a noticeable
pause.)

`I` toggles balance assertion checking. Disabling balance assertions
temporarily can be useful for troubleshooting.

`a` runs command-line hledger\'s add command, and reloads the updated
file. This allows some basic data entry.

`A` is like `a`, but runs the
[hledger-iadd](http://hackage.haskell.org/package/hledger-iadd) tool,
which provides a terminal interface. This key will be available if
`hledger-iadd` is installed in \$path.

`E` runs \$HLEDGER_UI_EDITOR, or \$EDITOR, or a default
(`emacsclient -a "" -nw`) on the journal file. With some editors (emacs,
vi), the cursor will be positioned at the current transaction when
invoked from the register and transaction screens, and at the error
location (if possible) when invoked from the error screen.

`B` toggles cost mode, showing amounts in their cost\'s commodity (like
toggling the [`-B/--cost`](https://hledger.org/hledger.html#b-cost)
flag).

`V` toggles value mode, showing amounts\' current market value in their
default valuation commodity (like toggling the
[`-V/--market`](https://hledger.org/hledger.html#v-market-value) flag).
Note, \"current market value\" means the value on the report end date if
specified, otherwise today. To see the value on another date, you can
temporarily set that as the report end date. Eg: to see a transaction as
it was valued on july 30, go to the accounts or register screen, press
`/`, and add `date:-7/30` to the query.

At most one of cost or value mode can be active at once.

There\'s not yet any visual reminder when cost or value mode is active;
for now pressing `b` `b` `v` should reliably reset to normal mode.

`q` quits the application.

Additional screen-specific keys are described below.

## SCREENS

At startup, hledger-ui shows a menu screen by default. From here you can
navigate to other screens using the cursor keys: `UP`/`DOWN` to select,
`RIGHT` to move to the selected screen, `LEFT` to return to the previous
screen. Or you can use `ESC` to return directly to the top menu screen.

You can also use a command line flag to specific a different startup
screen (`--cs`, `--bs`, `--is`, `--all`, or `--register=ACCT`).

### Menu

This is the top-most screen. From here you can navigate to several
screens listing accounts of various types. Note some of these may not
show anything until you have configured [account
types](/hledger.html#account-types).

### Cash accounts

This screen shows \"cash\" (ie, liquid asset) accounts (like
`hledger balancesheet type:c`). It always shows balances (historical
ending balances on the date shown in the title line).

### Balance sheet accounts

This screen shows asset, liability and equity accounts (like
`hledger balancesheetequity`). It always shows balances.

### Income statement accounts

This screen shows revenue and expense accounts (like
`hledger incomestatement`). It always shows changes (balance changes in
the period shown in the title line).

### All accounts

This screen shows all accounts in your journal (unless filtered by a
query; like `hledger balance`). It shows balances by default; you can
toggle showing changes with the `H` key.

### Register

This screen shows the transactions affecting a particular account. Each
line represents one transaction, and shows:

-   the other account(s) involved, in abbreviated form. (If there are
    both real and virtual postings, it shows only the accounts affected
    by real postings.)

-   the overall change to the current account\'s balance; positive for
    an inflow to this account, negative for an outflow.

-   the running total after the transaction. With the `H` key you can
    toggle between

    -   the period total, which is from just the transactions displayed
    -   or the historical total, which includes any undisplayed
        transactions before the start of the report period (and matching
        the filter query if any). This will be the running historical
        balance (what you would see on a bank\'s website, eg) if not
        disturbed by a query.

Transactions affecting this account\'s subaccounts will be included in
the register if the accounts screen is in tree mode, or if it\'s in list
mode but this account has subaccounts which are not shown due to a depth
limit. In other words, the register always shows the transactions
contributing to the balance shown on the accounts screen. Tree mode/list
mode can be toggled with `t` here also.

`U` toggles filtering by [unmarked status](hledger.html#status), showing
or hiding unmarked transactions. Similarly, `P` toggles pending
transactions, and `C` toggles cleared transactions. (By default,
transactions with all statuses are shown; if you activate one or two
status filters, only those transactions are shown; and if you activate
all three, the filter is removed.)

`R` toggles real mode, in which [virtual
postings](hledger.html#virtual-postings) are ignored.

`z` toggles nonzero mode, in which only transactions posting a nonzero
change are shown (hledger-ui shows zero items by default, unlike
command-line hledger).

Press `RIGHT` to view the selected transaction in detail.

### Transaction

This screen shows a single transaction, as a general journal entry,
similar to hledger\'s print command and journal format
(hledger_journal(5)).

The transaction\'s date(s) and any cleared flag, transaction code,
description, comments, along with all of its account postings are shown.
Simple transactions have two postings, but there can be more (or in
certain cases, fewer).

`UP` and `DOWN` will step through all transactions listed in the
previous account register screen. In the title bar, the numbers in
parentheses show your position within that account register. They will
vary depending on which account register you came from (remember most
transactions appear in multiple account registers). The #N number
preceding them is the transaction\'s position within the complete
unfiltered journal, which is a more stable id (at least until the next
reload).

On this screen (and the register screen), the `E` key will open your
text editor with the cursor positioned at the current transaction if
possible.

This screen has a limitation with showing file updates: it will not show
them until you exit and re-enter it. So eg to see the effect of using
the `E` key, currently you must: - press `E`, edit and save the file,
then exit the editor, returning to hledger-ui - press `g` to reload the
file (or use `-w/--watch` mode) - press `LEFT` then `RIGHT` to exit and
re-enter the transaction screen.

### Error

This screen will appear if there is a problem, such as a parse error,
when you press g to reload. Once you have fixed the problem, press g
again to reload and resume normal operation. (Or, you can press escape
to cancel the reload attempt.)

## TIPS

### Watch mode

One of hledger-ui\'s best features is the auto-reloading `-w/--watch`
mode. With this flag, it will update the display automatically whenever
changes are saved to the data files.

This is very useful when reconciling. A good workflow is to have your
bank\'s online register open in a browser window, for reference; the
journal file open in an editor window; and hledger-ui in watch mode in a
terminal window, eg:

``` shell
$ hledger-ui --watch --register checking -C
```

As you mark things cleared in the editor, you can see the effect
immediately without having to context switch. This leaves more mental
bandwidth for your accounting. Of course you can still interact with
hledger-ui when needed, eg to toggle cleared mode, or to explore the
history.

There are currently some limitations with `--watch`:

It may not work correctly for you, depending on platform or system
configuration. (Eg
[#836](https://github.com/simonmichael/hledger/issues/836).)

At least on mac, there can be a slow build-up of CPU usage over time,
until the program is restarted (or, suspending and restarting with
`CTRL-z` `fg` may be enough).

It will not detect file changes made by certain editors, such as
Jetbrains IDEs or `gedit`, or on certain less common filesystems. (To
work around, press `g` to reload manually, or try
[#1617](https://github.com/simonmichael/hledger/issues/1617)\'s
`fs.inotify.max_user_watches` workaround and let us know.)

If you are viewing files mounted from another machine, the system clocks
on both machines should be roughly in agreement.

### Debug output

You can add `--debug[=N]` to the command line to log debug output. This
will be logged to the file `hledger-ui.log` in the current directory. N
ranges from 1 (least output, the default) to 9 (maximum output).

## ENVIRONMENT

**COLUMNS** The screen width to use. Default: the full terminal width.

**LEDGER_FILE** The main journal file to use when not specified with
`-f/--file`. Default: `$HOME/.hledger.journal`.

## BUGS

We welcome bug reports in the hledger issue tracker (shortcut:
<http://bugs.hledger.org>), or on the #hledger chat or hledger mail list
(<https://hledger.org/support>).

Some known issues:

`-f-` doesn\'t work (hledger-ui can\'t read from stdin).

If you press `g` with large files, there could be a noticeable pause.

The Transaction screen does not update from file changes until you exit
and re-endter it (see SCREENS \> Transaction above).

`--watch` is not yet fully robust on all platforms (see Watch mode
above).

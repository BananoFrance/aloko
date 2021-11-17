If you have any question : Julien#4403 on discord

aloko is a banano fork of atto who is a tiny Nano wallet, which focuses on ease of use through
simplicity. Included is a rudimentary Go library to interact with Nano
nodes.

Disclaimer: I am no cryptographer and aloko has not been audited. I
cannot guarantee that aloko is free of security compromising bugs.

# Installation
You can download precompiled binaries from the [releases
page](https://github.com/BananoFrance/aloko/releases) or build aloko yourself
like this; go 1.15 or higher is required:

```shell
git clone 'https://github.com/BananoFrance/aloko.git'
cd aloko
go build ./cmd/aloko
# The aloko binary is now available at ./aloko. You could also install
# to ~/go/bin/ by executing "go install ./cmd/aloko".
```
# Usage
If you are on windows , you have to paste your seed after each command. It will be changed in a future release. 

```console
$ # The new command generates a new seed.
$ aloko new
D420296F5FEF486175FAA8F649DED00A5B0A096DB8D03972937542C51A7F296C
$ # Store it in your password manager:
$ pass insert nano
Enter password for nano: D420296F5FEF486175FAA8F649DED00A5B0A096DB8D03972937542C51A7F296C
Retype password for nano: D420296F5FEF486175FAA8F649DED00A5B0A096DB8D03972937542C51A7F296C

$ # The address command shows the address for an account.
$ pass nano | aloko address
ban_3cyb3rwp5ba47t5jdzm5o7apeduppsgzw8ockn1dqt4xcqgapta6gh5htnnh

$ # With address and all following commands you can also provide an
$ # alternative account index (default is 0):
$ pass nano | aloko -a 1 address
ban_1o3igdpf8c4msdgwcop71x4o16zzkhe4kyku4axdi8iwh8wh13e4fwgherik

$ # The balance command will receive pending funds automatically.
$ pass nano | aloko balance
Creating receive block for 1.025 from ban_34ymtnmhwseiex4eqf7nnf5wcyg44kknuuen5wwurm18ma91msf6e1pqo8hx... done
Creating receive block for 0.1 from ban_39nd8eksw1ia6aokn96z4uthocke47hfsx9gr31othm1nrfwnzmmaeehiccq... 
done
1.337 NANO

$ # Choosing a representative is important for keeping the network
$ # decentralized.
$ pass nano | aloko representative ban_1jr699mk1fi6mxy1y76fmuyf3dgms8s5pzcsge5cyt1az93x4n18uxjenx93
Creating change block... done

$ # To avoid accidental loss of funds, the send command requires
$ # confirmation, unless the -y flag is given:
$ pass nano | aloko send 0.1 ban_11zdqnjpisos53uighoaw95satm4ptdruck7xujbjcs44pbkkbw1h3zomns5
Send 0.1 (ba)NANO to ban_11zdqnjpisos53uighoaw95satm4ptdruck7xujbjcs44pbkkbw1h3zomns5? [y/N]: y
Creating send block... done

$ aloko -h
Usage:
	aloko -v
	aloko n[ew]
	aloko [-a ACCOUNT_INDEX] a[ddress]
	aloko [-a ACCOUNT_INDEX] b[alance]
	aloko [-a ACCOUNT_INDEX] r[epresentative] REPRESENTATIVE
	aloko [-a ACCOUNT_INDEX] [-y] s[end] AMOUNT RECEIVER

If the -v flag is provided, atto will print its version number.

The new subcommand generates a new seed, which can later be used with
the other subcommands.

The address, balance, representative and send subcommands expect a seed
as the first line of their standard input. Showing the first address of
a newly generated key could work like this:
aloko new | tee seed.txt | aloko address

The send subcommand also expects manual confirmation of the transaction,
unless the -y flag is given.

The address subcommand displays addresses for a seed, the balance
subcommand receives pending sends and shows the balance of an account,
the representative subcommand changes the account's representative and
the send subcommand sends funds to an address.

ACCOUNT_INDEX is an optional parameter, which must be a number between 0
and 4,294,967,295. It allows you to use multiple accounts derived from
the same seed. By default the account with index 0 is chosen.
```

# Technical details
SOON...

# Offline signing
SOON...

# Donations
If you want to show your appreciation for the original creator, you can donate at
`nano_1i7wsbehgwhxct91wpojr1j588ydikd64uc7p3kj54nofqioc6ydjopezf13`.
Original work : https://github.com/codesoap/atto

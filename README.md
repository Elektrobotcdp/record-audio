# record-audio
Record Audion right from the terminal(BAsh extended script to use 'pacat' CLI tool to record audion from screen /STDIN or from playback)


Add `~/.local/bin` to your `PATH` in `~/.bashrc`, then reload Bash:

```bash
grep -qxF 'export PATH="$HOME/.local/bin:$PATH"' ~/.bashrc || \
printf '\nexport PATH="$HOME/.local/bin:$PATH"\n' >> ~/.bashrc

source ~/.bashrc
```

Make the script executable:

```bash
chmod +x ~/.local/bin/record-audio
```

You should then be able to run:

```bash
record-audio
```

If Bash still can’t find it, check that the file exists and that the path is set:

```bash
ls -l ~/.local/bin/record-audio
echo "$PATH"
```

If you only want to remove the recording command’s `PATH` entry:

```bash
sed -i '/export PATH="\$HOME\/.local\/bin:\$PATH"/d' ~/.bashrc
source ~/.bashrc
```


The standalone files will still exist. Remove them with:

```bash
rm -f ~/.local/bin/record-audio 
```

To inspect your `.bashrc` before removing anything:

```bash
grep -nE 'mypacat|myuname|record-audio|\.local/bin' ~/.bashrc
```

Save it over `~/.local/bin/record-audio`, then make it executable:

```bash
chmod +x ~/.local/bin/record-audio
```

Run it with the default monitor:

```bash
record-audio
```

Or specify a monitor source and filename:

```bash
record-audio --device=SOURCE_NAME.monitor earpiece.wav
```

To find the exact monitor source name:

```bash
pactl list short sources
```

Use the source corresponding to your earpiece’s output; the `@DEFAULT_MONITOR@` special name records from the system’s current default output.

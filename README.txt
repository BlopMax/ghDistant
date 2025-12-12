Aller dans /.git/hooks et crée un fichier "pre-commit", dans ce fichier mettez ce code :

#!/bin/bash
# Add text + date if user select "y"
# Add this file in .git/hooks/ and name it 'pre-commit'
read -p "Ajout Date dans ce commit (y/[n]) ? " yn < /dev/tty
yn=${yn:n}
case $yn in
  [Yy]* )
    echo "commit vérifié le $(date)" >> "$GIT_DIR/../suivi/commitInfo.txt"
    exit 0
    ;;
  [Nn]* )
    exit 0
    ;;
esac
exit 0

Si vous avez tout bien fais, le hook sera automatiquement pris en compte.

## présentation

l'idée est de voir si on peut reverse lookup des fichier par leur contenue est donc avoir la liste des gent l'ebergeant 

## commande
cherche si un fichier existe sur ipfs le 2em arg est pour demander cb

```truc(){ipfs dht findprovs -n ${2:-1} $(ipfs add --only-hash $1 -q)}```

cherche une chaine de caracter contenue dans un fichier si elle est uploader sur ipfs 

```str(){echo "$1" > OwOtmp ; truc OwOtmp ${2:-1} ; rm OwOtmp}```

cherche si des fichier en commun sur le systeme actuel avec ipfs

```find  /  -readable -type f 2>/dev/null  |parallel 'ipfs dht findprovs -n 1 $(ipfs add --only-hash {} -q) > /dev/null && echo "{}"'```

stress la table
`crunch 1 5|parallel 'echo {} > {} ; VAR=$(ipfs dht findprovs -n 1 $(ipfs add --only-hash {} -q));echo {} $VAR; rm {}'`

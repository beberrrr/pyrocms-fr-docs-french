# Tags Lang 

Le Tag _lang_  permet d'acc�der aux param�tres de langue pour l'utilisateur connect�. Si aucun utilisateur n'est connect�, la langue du site par d�faut est utilis�e.

## lang:name

	{{ noparse }}{{ lang:name }}{{ /noparse }}

Retourne le nom complet de la langue courante.

### Exemple Output:

	English

## lang:folder

	{{ noparse }}{{ lang:folder }}{{ /noparse }}

Retourne le nom du dossier de la langue courante.

### Exemple Output:

	english
	
## lang:code

Retourne le code de langue du langage courant.

	{{ noparse }}{{ lang:code }}{{ /noparse }}

### Exemple Output:

	en
	
## lang:direction

Retourne le sens des langues de la langue courante.

	{{ noparse }}{{ lang:direction }}{{ /noparse }}

### Exemple:

	ltr
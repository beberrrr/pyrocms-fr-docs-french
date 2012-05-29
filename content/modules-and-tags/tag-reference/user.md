# Tags user

Le plugin <em>user</em> vous permet d'acc�der aux donn�es des utilisateurs et la logique.

## user:logged_in

	{{ noparse }}{{ user:logged_in }}{{ /noparse }}

V�rifie si l'utilisateur est connect� ou non. Peut �tre utilis� comme un tag pair pour limiter l'affichage de certain code d'utilisateurs enregistr�s, ou un tag unique qui renvoie TRUE ou FALSE selon que l'utilisateur est connect� po

### Attributs

<table cellpadding="0" cellspacing="0">
	<tbody>
		<tr>
			<th>Nom</th>
			<th>Default</th>
			<th>Requis</th>
			<th>Description</th>
		</tr>
		<tr>
			<td width="100">group</td>
			<td width="100">None</td>
			<td width="100">Non</td>
			<td>Group slug. V�rifie si un utilisateur est non seulement connect�, mais aussi un membre du groupe sp�cifi�.</td>
		</tr>
	</tbody>
</table>

### Exemple

	{{ noparse }}{{ if user:logged_in }}
	&lt;p&gt;This is just for logged in users.&lt;/p&gt;
{{ endif }}{{ /noparse }}

## user:not\_logged\_in

	{{ noparse }}{{ user:not_logged_in }}{{ /noparse }}

Identique � la fonction pr�c�dente, mais au lieu v�rifier si un utilisateur n'est pas connect�. Prend �galement le param�tre _group_. Doivent �tre utilis�s dans un tag pair.

## Variables simples de profil utilisateur

Le plugin user vous donne �galement acc�s � des variables des diff�rents users utilisant la syntaxe suivante:

	{{ noparse }}{{ user:<em>variable</em> }}{{ /noparse }}

Ces appels par d�faut au user connect�, mais vous pouvez �galement sp�cifier l'ID d'un user avec le param�tre <em>user_id</em>:

	{{ noparse }}{{ user:<em>variable</em> user_id="4" }}{{ /noparse }}

Si vous utilisez des champs de flux personnalis�s qui retournent plusieurs enregistrements, vous pouvez acc�der aux valeurs � l'int�rieur comme des tag pairs:

	{{ noparse }}{{ user:country }}{{ name }} {{ /user:country }}{{ /noparse }}

Voici un tableau de variables qui sont cod�es en dur dans le syst�me et toujours disponible.

<table cellpadding="0" cellspacing="0">
	<tbody>
		<tr>
			<th>Variable</th>
			<th>Notes</th>
		</tr>
		<tr>
			<td width="200">id</td>
			<td>&nbsp;</td>
		</tr>
		<tr>
			<td width="200">group_id</td>
			<td>&nbsp;</td>
		</tr>
		<tr>
			<td width="200">ip_address</td>
			<td>&nbsp;</td>
		</tr>
		<tr>
			<td width="200">active</td>
			<td>1 or 0.</td>
		</tr>
		<tr>
			<td width="200">activation_code</td>
			<td>&nbsp;</td>
		</tr>
		<tr>
			<td width="200">created_on</td>
			<td>Unix epoch format.</td>
		</tr>
		<tr>
			<td width="200">last_login</td>
			<td>Unix epoch format.</td>
		</tr>
		<tr>
			<td width="200">username</td>
			<td>&nbsp;</td>
		</tr>
		<tr>
			<td width="200">display_name</td>
			<td>&nbsp;</td>
		</tr>
		<tr>
			<td width="200">forgotten_password_code</td>
			<td>&nbsp;</td>
		</tr>
		<tr>
			<td width="200">remember_code</td>
			<td>&nbsp;</td>
		</tr>
		<tr>
			<td width="200">group</td>
			<td>Group slug.</td>
		</tr>
		<tr>
			<td width="200">group_description</td>
			<td>Group name.</td>
		</tr>
	</tbody>
</table>

## user:profile

Mis � part l'acc�s � des champs du profil utilisateur individuel, vous pouvez �galement y acc�der en utilisant la fonction de profil. A l'int�rieur du tag pair, vous pouvez acc�der � l'une des variables de profil utilisateur, y compris vos champs personnalis�s.

	{{ noparse }}{{ user:profile }}

	{{ display_name }}

	{{ custom_field }}

	{{ custom_field:sub_value }}

{{ /user:profile }}{{ /noparse }}

La balise de profil prend �galement une valeur facultative user_id.

	{{ noparse }}{{ user:profile user_id="4" }}{{ /noparse }}

## user:profile\_fields

Dans le cas o� vous voulez juste vous montrer toutes les donn�es de profil utilisateur dans une liste, vous pouvez le faire avec cette fonction. Chaque �l�ment de donn�es utilisateur peuvent �tre accessibles via les variables suivantes:

<table>
	<tr>
		<td>value</td>
		<td>La valeur du champs. Pour les champs du profil utilisateur qui retournent plusieurs valeurs, ce sera l'affichage alternatif canonique que les types de terrain peut et doit fournir.</td>
	</tr>
	<tr>
		<td>name</td>
		<td>Nom du champs .</td>
	</tr>
	<tr>
		<td>slug</td>
		<td>champs slug.</td>
	</tr>
</table>

	{{ noparse }}{{ user:profile_fields }}

	&lt;p>&lt;strong>{{ name }}: {{ value }}&lt;/strong>&lt;/p>

{{ /user:profile_fields }}{{ /noparse }}

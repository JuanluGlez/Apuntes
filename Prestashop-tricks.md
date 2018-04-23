# Prestashop Tricks

## Formulario de contacto
### Activar por defecto checkbox de newsletter

Editamos esta línea en el `autentification.tpl`:
`type="checkbox" name="newsletter" id="newsletter" value="1" {if isset($smarty.post.newsletter) AND $smarty.post.newsletter == 1} checked="checked"{/if}`

por esta

`type="checkbox" name="newsletter" id="newsletter" value="1" {if !sizeof($errors) OR (sizeof($errors) AND $smarty.post.newsletter == 1)} checked="checked"{/if}`
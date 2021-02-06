# vim tricks

## **Replace selection everywhere**

`:%s/polo/perin/g`

## **Dans le cas d'un espace :**

`%s/name.d/bind\/name.d/g`

`%s#thisworks#too#g`

## **Commanter plusieurs ligne \(par ex\)**

`:line_number_start,line_number_ends/^/#/g`

## **Afficher le nombre de lignes ::**

`:set nu`

## **Run a command**

`%! ls`

## **Select chars and delete \(ex 1st char\) :**

control-V -&gt; selection -&gt; Hit x

## **Delete something and repeat on every lines :**

`shift+A --→ action → enter -→ . (dot on every lines)`


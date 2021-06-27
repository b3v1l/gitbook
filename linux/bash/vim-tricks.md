# vim tricks

## **Replace selection everywhere**

```text
:%s/polo/perin/g
```

## **Dans le cas d'un espace :**

```csharp
%s/name.d/bind\/name.d/g
%s#thisworks#too#g
```

## **Commanter plusieurs ligne \(par ex\)**

```csharp
:line_number_start,line_number_ends/^/#/g
:13,39s/^/#/g
```

## **Display line numbers**

```csharp
:set nu

disable
:set nonumber
```

## **Run a command**

```csharp
%! ls
```

### Go to char X in the current line

```csharp
1000 | 
```

## **Select chars and delete \(ex 1st char\) :**

control-V -&gt; selection -&gt; Hit x

## **Delete something and repeat on every lines :**

`shift+A --→ action → enter -→ . (dot on every lines)`


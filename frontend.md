# Kadromierz Frontend Style Guide

<details markdown="1">
  <summary>Table of Contents</summary>

- [1 Lista nieużywanych rzeczy](#s1-can-be-removed)
- [2 Używanie typescript](#s2-typescipt-usage)
  - [2.1 Indexed Access Types](#s2.1-indexed-access-types)
  - [2.2 Pick](#s2.2-pick)
  - [2.3 Ostrzeżenia](#2.3-warnings)

</details>

<a id="#s1-can-be-removed"></a>

## 1 Lista nieużywanych rzeczy

Poniżej wypisane są komponenty, widoki oraz funkcjonalności, które kiedyś były używane, a obecnie nikt z nich nie korzysta i można je usuwać przy zadaniach albo refaktorze kodu.

- Wersja demo aplikacji

<a id="s2-typescipt-usage"></a>

## 2 Używanie typescript

<a id="s2.1-indexed-access-types"></a>

Aby uniknąć tworzenia wielu nazw dla typów oraz unikania podstawowych typów dla obiektów, które są wielokrotnie używane należy stosować index access types, np:

```typescript
date: EmploymentConditions['hire_date'],
```

### 2.1 Indexed Access Types

W przypadku tworzenia typu dla obiektu, który ma wiele wspólnych pól już z istniejącym typem należy używać Pick, np:

<a id="s2.2-pick"></a>

### 2.2 Pick

```typescript
type X = {
    name: string,
    age: number,
    color: string,
    ...
}

export type Y = {
    id: string,
    ...
} & Pick<
  X,
  | 'name'
  | 'age'
>;

```

<a id="s2.3-warnings"></a>

### 2.3 Ostrzeżenia

Niektóre typy pomimo, że nazwę mają podobną mogą różnić się strukturą, np.:

- UserEmployee !== Employee
- Warunki zatrudnienia dla Employee nie mają takiej samej struktury jak pojedynczy obiekt z employmentConditions

---
id: generics-dart
slug: generics-dart
title: Generics em Dart
sidebar_position: 1
tags:
    - generics
    - tipos
---

# Introdução a Generics

## O que são Generics?

Generics são uma característica fundamental em Dart que permitem criar código flexível e reutilizável, permitindo que funções, classes e métodos operem com diferentes tipos de dados sem sacrificar a segurança de tipos.

## Por que usar Generics em Dart?

Usar Generics torna o código mais genérico, flexível e seguro em relação a tipos. Isso reduz a duplicação de código e melhora a legibilidade.

### Vantagens de usar Generics

<ul>
<li>Reutilização de código.</li>
<li>Maior segurança de tipos.</li>
<li>Maior flexibilidade.</li>
</ul>

## Sintaxe Básica

Em Dart, você pode declarar classes, funções e métodos genéricos usando o operador `<T>`, onde "T" é um tipo genérico.

```dart title="meuTipoGenerico.dart"s
class MeuTipoGenerico<T>{
  T _value;

  MeuTipoGenerico(T value) : _value = value;

  T get value => _value;

  @override
  String toString() {
    var runtimeType = _value.runtimeType;
    return "[${runtimeType.toString()}]: $_value";
  }
}
```

## Usando o operador `<>` para especificar tipos genéricos

Ao criar instâncias genéricas, você deve especificar o tipo dentro dos parênteses angulares.

```dart title="main.dart"
import 'meuTipoGenerico.dart';

void main(List<String> args){
  MeuTipoGenerico<String> meuTipoString = MeuTipoGenerico("10");
  MeuTipoGenerico<int> meuTipoInt = MeuTipoGenerico(10);

  print(meuTipoString);
  print(meuTipoInt);
}
```
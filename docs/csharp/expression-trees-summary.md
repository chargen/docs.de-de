---
title: Zusammenfassung der Ausdrucksbaumstrukturen
description: Dieser Beitrag fasst zusammen, wie Sie Ausdrucksbaumstrukturen verwenden können, um dynamische Programme zu erstellen, die Code wie Daten interpretieren, und um neue Funktionen basierend auf diesem Code zu erstellen.
ms.date: 06/20/2016
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: e0d46aa67b61fd4e1d2bcc20b4a567524bb00301
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="expression-trees-summary"></a>Zusammenfassung der Ausdrucksbaumstrukturen

[Vorheriges – Übersetzen von Ausdrücken](expression-trees-translating.md)

In dieser Serie haben Sie erfahren, wie Sie *Ausdrucksbaumstrukturen* verwenden können, um dynamische Programme zu erstellen, die Code wie Daten interpretieren, und um neue Funktionen basierend auf diesem Code zu erstellen.

Sie können Ausdrucksbaumstrukturen untersuchen, um die Absicht eines Algorithmus zu verstehen. Sie können nicht nur diesen Code überprüfen. Sie können neue Ausdrucksbaumstrukturen erstellen, die geänderte Versionen des ursprünglichen Codes darstellen.

Sie können auch mithilfe von Ausdrucksbaumstrukturen einen Algorithmus betrachten und den Algorithmus in eine andere Sprache oder Umgebung übersetzen. 

## <a name="limitations"></a>Einschränkungen

Es gibt einige neuere C#-Sprachelemente, die nicht gut in Ausdrucksbaumstrukturen übersetzt werden. Ausdrucksbaumstrukturen können keine `await`-Ausdrücke oder `async`-Lambdaausdrücke enthalten. Viele der in der C# 6-Version hinzugefügten Funktionen werden nicht genau wie in den Ausdrucksbaumstrukturen geschrieben angezeigt. Stattdessen werden neuere Funktionen in Ausdrucksbaumstrukturen in der entsprechenden früheren Syntax verfügbar gemacht. Diese sind möglicherweise nicht so sehr von einer Einschränkung betroffen, wie Sie vielleicht denken. In der Tat bedeutet dies, dass Ihr Code, der Ausdrucksbaumstrukturen interpretiert, wahrscheinlich immer noch genauso funktioniert, wenn neue Sprachfunktionen eingeführt werden.

Trotz dieser Einschränkungen können Ausdrucksbaumstrukturen es Ihnen ermöglichen, dynamische Algorithmen zu erstellen, die sich auf das Interpretieren und Bearbeiten von Code verlassen, der als Datenstruktur dargestellt wird. Es ist ein leistungsfähiges Tool und eine der Funktionen des .NET-Ökosystems, die es umfangreichen Bibliotheken wie Entity Framework ermöglichen, zu erreichen, was sie tun.


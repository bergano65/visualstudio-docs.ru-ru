---
title: "Практическое руководство. Использование функции Windows ReadFile (Руководство по программированию на C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ReadFile - функция [C#]"
ms.assetid: 46bb53e0-a658-48c9-ae36-6720da7781c1
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "billchi"
manager: "douge"
---
# Практическое руководство. Использование функции Windows ReadFile (Руководство по программированию на C#)
Следующий пример демонстрирует использование функции Windows `ReadFile` путем чтения и отображения текстового файла.  Для функции `ReadFile` требуется использовать код `unsafe`, поскольку для функции требуется указатель в качестве параметра.  
  
 Массив байт, передающийся в функцию `Read`, является управляемым типом.  Это означает, что сборщик мусора среды CLR может произвольным образом перемещать память, используемую массивом.  Во избежание этого блок [fixed](/dotnet/csharp/language-reference/keywords/fixed-statement) используется для получения указателя на память и его пометки таким образом, что его не смог переместить сборщик мусора.  В конце блока `fixed` память снова становится доступной для перемещения путем сборки мусора.  
  
 Эта способность называется *декларативным закреплением*.  При закреплении излишние расходы памяти практически исключены, за исключением случаев, когда в блоке `fixed` выполняется сборка мусора, что весьма маловероятно.  Тем не менее, закрепление может привести к некоторым нежелательным побочным эффектам при запуске глобальной сборки мусора.  Способность сборщика мусора сжимать память резко ограничивается закрепленными буферами.  Поэтому следует избегать закрепления, если это возможно.  
  
## Пример  
 [!code-cs[csProgGuidePointers#2](../misc/codesnippet/CSharp/how-to-use-the-windows-readfile-function-csharp-programming-guide_1.cs)]  
  
## См. также  
 [Руководство по программированию на C\#](/dotnet/csharp/programming-guide/index)   
 [Справочник по C\#](/dotnet/csharp/language-reference/index)   
 [Небезопасный код и указатели](/dotnet/csharp/programming-guide/unsafe-code-pointers/index)   
 [Типы указателей](/dotnet/csharp/programming-guide/unsafe-code-pointers/pointer-types)   
 [Garbage Collection](../Topic/Garbage%20Collection.md)
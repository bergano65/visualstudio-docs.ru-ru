---
title: "SDK для доступа к интерфейсу отладки | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "отладка [пакет SDK для доступа к интерфейсу отладки]"
  - "отладчик [пакет SDK для доступа к интерфейсу отладки]"
  - "пакет SDK для доступа к интерфейсу отладки"
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# SDK для доступа к интерфейсу отладки
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Пакет средств разработки программного обеспечения доступа к интерфейсу отладки \(Майкрософт\) SDK для доступа к интерфейсу отладки\) предоставляет доступ для отладки сведения, хранящиеся в файлах базы данных программы \(pdb\), создаваемых средствами postcompiler Майкрософт.  Поскольку формат pdb\-файла, создаваемого средствами postcompiler передает постоянное изменение предоставлять формат непрактичен.  Использование API DIA можно разрабатывать приложения, которые выполняют поиск и просмотр отладочных сведений, хранящихся в файле pdb.  Такие приложения можно, например, создать отчет об данные для выполнения трассировку\-Назад стека и анализировать данные о производительности.  
  
## В этом подразделе  
 [Начало работы](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)  
 Предоставляет общие сведения о функциях SDK для доступа к интерфейсу отладки и указывает расположение пакета SDK для доступа к интерфейсу отладки устанавливается а также необходимые файлы заголовка и библиотеки.  
  
 [Запрос PDB\-файла](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Предоставляет инструкции по использованию API DIA, чтобы запросить файл pdb.  
  
 [Символы и теги символов](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)  
 Описание символов и символов в теги используются API DIA.  
  
 [Справочник](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)  
 Содержит интерфейсы, методы перечисления и структуры API DIA.  
  
 [Пример файла Dia2dump](../../debugger/debug-interface-access/dia2dump-sample.md)  
 Показывает, как использовать API DIA для поиска и просматривать отладочные сведения.  
  
 [Файл исходного кода Dia2dump.cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)  
 Исходный код, используемый by [Пример файла Dia2dump](../../debugger/debug-interface-access/dia2dump-sample.md) демонстрация API DIA.
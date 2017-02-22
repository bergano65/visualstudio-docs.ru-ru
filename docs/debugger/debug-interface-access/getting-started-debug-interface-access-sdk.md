---
title: "Начало работы (SDK для доступа к интерфейсу отладки) | Microsoft Docs"
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
  - "DBG-файлы"
  - "DBG-файлы"
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Начало работы (SDK для доступа к интерфейсу отладки)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Предоставляет пакет SDK для доступа к интерфейсу отладки \(DIA\) с учебной документации и образцом, которая иллюстрирует, как использовать API DIA.  Используйте интерфейсы и методы в пакет SDK для доступа к интерфейсу отладки для разработки пользовательских приложений, которые открыты pdb\- и .dbg и их содержимого для поиска символьных значений атрибутов, адреса и другие данные отладки.  Это пакет SDK предоставляет также ссылочные таблицы для свойств, связанных с символов, найденные в приложениях C\+\+.  
  
 Для эффективного использования использовании пакета SDK для доступа к интерфейсу отладки, необходимо ознакомиться со следующим:  
  
-   Язык программирования C\+\+  
  
-   Программирование модели COM  
  
-   Интегрированная среда разработки Visual Studio ide\), компилирование образца  
  
 Пакет SDK для доступа к интерфейсу отладки обычно устанавливается вместе с Visual Studio и ее расположение по умолчанию *\[диск\]*\\ Program files \\ Microsoft Visual Studio 9,0 \\ SDK для доступа к интерфейсу отладки.  Как часть установки msdia90.dll, который реализует пакет SDK для доступа к интерфейсу отладки автоматически регистрируется поэтому все, что нужно сделать, чтобы использовать его для включения `dia2.h` в программе и ссылки  `diaguids.lib`.  
  
 Заголовок: включите \\ dia2.h  
  
 Библиотеки: lib \\ diaguids.lib  
  
 Библиотеки DLL: bin \\ msdia80.dll  
  
 IDL. idl \\ dia2.idl  
  
## Содержание  
 [Обзор](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 Просматривает базовую архитектуру DIA.  
  
 [Запрос PDB\-файла](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Содержит пошаговые инструкции по использованию API DIA, чтобы запросить файл pdb.  
  
## См. также  
 [SDK для доступа к интерфейсу отладки](../../debugger/debug-interface-access/debug-interface-access-sdk.md)
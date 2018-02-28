---
title: "SDK для доступа к интерфейсу отладки | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- debugging [DIA SDK]
- debugger [DIA SDK]
- DIA SDK
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: cd84741d006304f7dfefe8ee4a1060ba64ffdb8b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="debug-interface-access-sdk"></a>SDK для доступа к интерфейсу отладки
Microsoft отладки интерфейс средств разработки программного обеспечения (SDK для доступа к интерфейсу отладки) предоставляет доступ к отладочной информации, хранящейся в файлах базы данных (.pdb) программ средствами обработки после компиляции Microsoft. Так как формат PDB-файл, создаваемых средствами подвергаются константой редакции, предоставление доступа к формат оказывается нецелесообразным. С помощью API доступа к интерфейсу отладки, можно разрабатывать приложения, которые поиск и просматривать отладочной информации, хранящейся в PDB-файл. Такие приложения например, сообщающие сведения обратной трассировки стека и анализировать данные о производительности.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Начало работы](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)  
 Обзор пакета SDK для доступа к интерфейсу отладки функций и определяет, где установлен пакет SDK для, а также необходимых файлов заголовков и библиотек.  
  
 [Запрос PDB-файла](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Инструкции по использованию API доступа к интерфейсу отладки в PDB-файл запрос.  
  
 [Символы и теги символов](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)  
 Описывает, как символы и теги символов используются в интерфейсе API для доступа к интерфейсу отладки.  
  
 [Ссылки](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)  
 Содержит интерфейсы, методы, перечисления и структуры, интерфейса API доступа к интерфейсу отладки.  
  
 [Пример файла Dia2dump](../../debugger/debug-interface-access/dia2dump-sample.md)  
 Показывает, как использовать API доступа к интерфейсу отладки для поиска и просмотреть сведения об отладке.  
  
 [Файл исходного кода Dia2dump.cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)  
 Исходный код, используемый [Dia2dump-пример](../../debugger/debug-interface-access/dia2dump-sample.md) для демонстрации API доступа к интерфейсу отладки.
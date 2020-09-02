---
title: SDK для доступа к интерфейсу отладки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging [DIA SDK]
- debugger [DIA SDK]
- DIA SDK
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ddaea95bc879364de99c0ec01213cda30fa4e7d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197626"
---
# <a name="debug-interface-access-sdk"></a>SDK для доступа к интерфейсу отладки
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Пакет средств разработки программного обеспечения для доступа к интерфейсу Microsoft Debug (DIA SDK) предоставляет доступ к отладочной информации, хранящейся в файлах базы данных программы (PDB), созданных средствами Microsoft Compiler. Так как формат PDB-файла, создаваемого средствами компилятора, является постоянной версией, непрактичный доступ к этому формату нецелесообразн. С помощью API DIA можно разрабатывать приложения, которые выполняют поиск и просмотрируют отладочную информацию, хранящуюся в PDB-файле. Такие приложения могут, например, сообщать о трассировке стека для обратной передачи и анализировать данные производительности.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Начало работы](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)  
 Содержит общие сведения о функциях пакета SDK DIA и указывает, где установлен пакет SDK DIA, а также необходимые файлы заголовка и библиотеки.  
  
 [Запрос PDB-файла](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Содержит инструкции по использованию API DIA для запроса PDB-файла.  
  
 [Символы и теги символов](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)  
 Описывает, как символы и теги символов используются в API DIA.  
  
 [Ссылки](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)  
 Содержит интерфейсы, методы, перечисления и структуры API DIA.  
  
 [Пример файла Dia2dump](../../debugger/debug-interface-access/dia2dump-sample.md)  
 Демонстрирует использование API DIA для поиска и просмотра отладочной информации.  
  
 [Файл исходного кода Dia2dump.cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)  
 Исходный код, используемый [примером файла Dia2dump](../../debugger/debug-interface-access/dia2dump-sample.md) для демонстрации API DIA.

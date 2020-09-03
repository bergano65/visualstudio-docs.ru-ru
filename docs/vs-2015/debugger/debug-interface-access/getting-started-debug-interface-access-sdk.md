---
title: Начало работы (SDK для доступа к интерфейсу отладки) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- .dbg files
- DBG files
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 54f83f00ed2e99d1541e15092cb3ee0ce9e08952
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164172"
---
# <a name="getting-started-debug-interface-access-sdk"></a>Начало работы (SDK для доступа к интерфейсу отладки)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Пакет SDK для доступа к интерфейсу отладки (DIA) содержит документацию с инструкциями и пример, демонстрирующий использование API DIA. Используйте интерфейсы и методы в пакете SDK DIA для разработки пользовательских приложений, открывающих файлы PDB и DBG, и поиска в содержимом символов, значений, атрибутов, адресов и других отладочных данных. Этот пакет SDK также содержит справочные таблицы по свойствам, связанным с символами, найденными в приложениях C++.  
  
 Для лучшего использования пакета SDK для DIA необходимо ознакомиться со следующими разрешениями:  
  
- Язык программирования C++  
  
- Программирование COM  
  
- Интегрированная среда разработки (IDE) Visual Studio для компиляции образцов  
  
  Пакет SDK DIA обычно устанавливается вместе с Visual Studio, и его расположение по умолчанию — *[диск]* \Program Files\Microsoft Visual Studio 9.0 \ DIA SDK. В рамках установки msdia90.dll, который реализует пакет SDK для DIA, автоматически регистрируется, так что все, что необходимо для его использования, — включить `dia2.h` в программу и привязать к `diaguids.lib` .  
  
  Заголовок: include\dia2.h  
  
  Библиотека: либ\диагуидс.либ  
  
  DLL: bin\msdia80.dll  
  
  IDL: idl\dia2.idl  
  
## <a name="in-this-section"></a>в этом разделе  
 [Обзор](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 Проверяет базовую архитектуру DIA.  
  
 [Запрос PDB-файла](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Содержит пошаговые инструкции по использованию API DIA для запроса PDB-файла.  
  
## <a name="see-also"></a>См. также:  
 [SDK для доступа к интерфейсу отладки](../../debugger/debug-interface-access/debug-interface-access-sdk.md)

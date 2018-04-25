---
title: Приступая к работе (доступа к интерфейсу отладки SDK) | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- .dbg files
- DBG files
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1fdfe560f22374c0b46305d096bea32a784babe6
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="getting-started-debug-interface-access-sdk"></a>Начало работы (SDK для доступа к интерфейсу отладки)
Отладка Interface Access (DIA) пакет SDK предоставляет документацию инструкции и образец, в котором показано, как использовать API-Интерфейс доступа к интерфейсу отладки. Используйте интерфейсы и методы в пакете SDK для доступа к интерфейсу отладки при разработке пользовательских приложений, откройте файлы PDB-файл и .dbg и искать их содержимое для символов, значения, атрибуты, адреса и другие отладочную информацию. Этот пакет SDK также предоставляет ссылочные таблицы для свойства, связанные с использованием символов, содержащихся в приложениях C++.  
  
 Чтобы лучше всего использовать пакет SDK для доступа к интерфейсу отладки, необходимо ознакомиться со следующими:  
  
-   Язык программирования C++  
  
-   Программирование COM.  
  
-   Разработки среды Visual Studio (IDE) для компиляции образцов  
  
 ПАКЕТ SDK для обычно устанавливается вместе с Visual Studio и расположения по умолчанию — *[диск]* \Program Files\Microsoft 9.0\DIA Visual Studio SDK. Как часть установки, msdia90.dll, реализующий пакет SDK для доступа к интерфейсу отладки, автоматически регистрируется, поэтому все, что необходимо сделать, чтобы использовать его для включения `dia2.h` в программе и ссылку на `diaguids.lib`.  
  
 Заголовок: include\dia2.h  
  
 Библиотека: lib\diaguids.lib  
  
 Библиотека DLL: bin\msdia80.dll  
  
 IDL: idl\dia2.idl  
  
## <a name="in-this-section"></a>В этом разделе  
 [Обзор набора средств Visual Studio для Unity](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 Просматривает основная архитектура доступа  
  
 [Запрос PDB-файла](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Содержит пошаговые инструкции по использованию API доступа к интерфейсу отладки в PDB-файл запрос.  
  
## <a name="see-also"></a>См. также  
 [SDK для доступа к интерфейсу отладки](../../debugger/debug-interface-access/debug-interface-access-sdk.md)
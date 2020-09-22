---
title: Исключение файлов ~ SAK | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 751acf4e5f56b7b477f05ab71571e0becd566649
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842512"
---
# <a name="elimination-of-sak-files"></a>Устранение ~SAK-файлов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В API подключаемого модуля системы управления версиями 1,2 файлы ~ SAK были заменены флагами возможностей и новыми функциями, которые определяют, поддерживает ли подключаемый модуль системы управления версиями файл МССККПРЖ и общие извлечения.  
  
## <a name="sak-files"></a>~ SAK файлы  
 Visual Studio .NET 2003 создал временные файлы с префиксом ~ SAK. Эти файлы используются для определения того, поддерживает ли подключаемый модуль системы управления версиями:  
  
- МССККПРЖ. Файл SCC.  
  
- Множественные (Общие) извлечения.  
  
  Для подключаемых модулей, поддерживающих расширенные функции, предоставляемые в API подключаемого модуля системы управления версиями 1,2, интегрированная среда разработки может обнаружить эти возможности, не создавая временные файлы с помощью новых возможностей, флагов и функций, подробно описанных в следующих разделах.  
  
## <a name="new-capability-flags"></a>Новые флаги возможностей  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## <a name="new-functions"></a>Новые функции  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 Если подключаемый модуль системы управления версиями поддерживает множественные (Общие) извлечения, то он объявляет `SCC_CAP_MULTICHECKOUT` возможность и реализует `SccIsMultiCheckOutEnabled` функцию. Эта функция вызывается при каждом выполнении операции извлечения в любом из проектов, находящихся в системе управления версиями.  
  
 Если подключаемый модуль системы управления версиями поддерживает создание и использование МССККПРЖ. Файл SCC, он объявляет `SCC_CAP_SCCFILE` возможность и реализует [скквиллкреатесккфиле](../../extensibility/sccwillcreatesccfile-function.md). Эта функция вызывается со списком файлов. Функция возвращает `TRUE/FALSE` для каждого файла, чтобы указать, следует ли использовать мссккпрж в Visual Studio. Файл SCC. Если подключаемый модуль системы управления версиями не поддерживает эти новые возможности и функции, для отключения создания этих файлов можно использовать следующий раздел реестра:  
  
 [HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl] "Доноткреатетемпорарифилесинсаурцеконтрол" = DWORD: 00000001  
  
> [!NOTE]
> Если этот раздел реестра имеет значение типа DWORD: 00000000, то он эквивалентен несуществующему ключу, и Visual Studio по-прежнему пытается создать временные файлы. Однако если для раздела реестра задано значение DWORD: 00000001, Visual Studio не пытается создать временные файлы. Вместо этого предполагается, что подключаемый модуль системы управления версиями не поддерживает МССККПРЖ. Файл SCC и не поддерживает общие извлечения.  
  
## <a name="see-also"></a>См. также:  
 [Новые возможности в API версии 1.2 подключаемого модуля системы управления версиями](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

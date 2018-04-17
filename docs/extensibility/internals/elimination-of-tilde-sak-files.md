---
title: Устранение ~ файлы SAK | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 61227652bf191280f69466f127c4a400ea43856e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="elimination-of-sak-files"></a>Устранение ~ SAK файлов
В версии 1.2 API подключаемого модуля управления источника ~ SAK файлы были заменены флаги возможностей и новые функции, определить, поддерживает ли подключаемый модуль системы управления версиями файлов MSSCCPRJ и общие извлечения.  
  
## <a name="sak-files"></a>~ SAK файлов  
 Visual Studio .NET 2003 созданы временные файлы с префиксом ~ SAK. Эти файлы используются, чтобы определить, поддерживает ли подключаемый модуль системы управления версиями:  
  
-   MSSCCPRJ. Файл SCC.  
  
-   Несколько одновременных извлечений (совместно используемые).  
  
 Для подключаемых модулей, поддерживающие расширенные функции в версии 1.2 API для управления подключаемого модуля источника интегрированной среды разработки может обнаруживать эти возможности без создания временных файлов за счет использования новых возможностей, флаги и функции, описанные в следующих разделах.  
  
## <a name="new-capability-flags"></a>Флаги новых возможностей  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## <a name="new-functions"></a>Новые функции  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 Если подключаемый модуль системы управления версиями поддерживает несколько одновременных извлечений (совместно используемые), то он объявляет `SCC_CAP_MULTICHECKOUT` возможностей и реализует `SccIsMultiCheckOutEnabled` функции. Эта функция вызывается при каждой операции извлечения на любом из проектов, контролируемых системой управления версиями.  
  
 Если подключаемый модуль системы управления версиями поддерживает создание и использование MSSCCPRJ. Файл SCC, то оно объявляет `SCC_CAP_SCCFILE` возможностей и реализует [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Эта функция вызывается со списком файлов. Функция возвращает `TRUE/FALSE` для каждого файла указать, следует ли использовать MSSCCPRJ Visual Studio. Файл SCC для него. Если подключаемый модуль системы управления версиями решает не поддерживает эти новые возможности и функции, его можно использовать следующий раздел реестра для отключения создания этих файлов:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] «DoNotCreateTemporaryFilesInSourceControl» = DWORD: 00000001  
  
> [!NOTE]
>  Если этот раздел реестра имеет значение DWORD: 00000000, это эквивалентно, несуществующего ключа и Visual Studio по-прежнему пытается создать временные файлы. Тем не менее если раздел реестра имеет значение DWORD: 00000001, Visual Studio не пытается создать временные файлы. Вместо них предполагается, что подключаемый модуль системы управления версиями не поддерживает MSSCCPRJ. Файл SCC и не поддерживает общие извлечения.  
  
## <a name="see-also"></a>См. также  
 [Новые возможности в API версии 1.2 подключаемого модуля системы управления версиями](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
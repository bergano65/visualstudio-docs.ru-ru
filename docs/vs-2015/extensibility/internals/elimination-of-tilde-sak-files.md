---
title: Устранение ~ SAK-файлов | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c7422b0dae02b12d731713f6da416361798d3276
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49824315"
---
# <a name="elimination-of-sak-files"></a>Устранение ~SAK-файлов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В версии 1.2 API подключаемого модуля управления источника ~ SAK-файлов были заменены флаги возможностей и новые функции, которые позволяют обнаружить, поддерживает ли подключаемый модуль системы управления версиями файл MSSCCPRJ и общими извлеченными элементами.  
  
## <a name="sak-files"></a>~ SAK-файлов  
 Visual Studio .NET 2003 создан временные файлы, которые начинаются с префикса ~ SAK. Эти файлы используются, чтобы определить, поддерживает ли подключаемый модуль системы управления версиями:  
  
- MSSCCPRJ. Файл SCC.  
  
- Несколько одновременных извлечений (совместно используемые).  
  
  Подключаемые модули, которые поддерживают расширенные функции, доступные в версии 1.2 подключаемого модуля для API управления источника интегрированной среды разработки может обнаруживать эти возможности без создания временных файлов при помощи новых возможностей, флагов и функции, описанные в следующих разделах.  
  
## <a name="new-capability-flags"></a>Новые флаги возможностей  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## <a name="new-functions"></a>Новые функции  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 Если подключаемый модуль системы управления версиями поддерживает несколько одновременных извлечений (совместно используемые), то он объявляет `SCC_CAP_MULTICHECKOUT` возможности и реализует `SccIsMultiCheckOutEnabled` функции. Эта функция вызывается, когда операция извлечения происходит на любом из проектов, контролируемых системой управления версиями.  
  
 Если подключаемый модуль системы управления версиями поддерживает создание и использование MSSCCPRJ. Файл SCC, то он объявляет `SCC_CAP_SCCFILE` возможности и реализует [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Эта функция вызывается с помощью списка файлов. Функция возвращает `TRUE/FALSE` для каждого файла указать, следует ли использовать MSSCCPRJ Visual Studio. Файл SCC для него. Если подключаемый модуль системы управления версиями решил не поддерживает эти новые возможности и функции, его можно использовать следующий раздел реестра для отключения создания этих файлов:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] «DoNotCreateTemporaryFilesInSourceControl» = DWORD: 00000001  
  
> [!NOTE]
>  Если этот раздел реестра имеет значение DWORD: 00000000, это эквивалентно, несуществующий ключ и Visual Studio по-прежнему пытается создать временные файлы. Тем не менее если раздел реестра имеет значение DWORD: 00000001, Visual Studio не пытается создать временные файлы. Вместо этого предполагается, что подключаемый модуль системы управления версиями не поддерживает MSSCCPRJ. Файл SCC и не поддерживает общие извлечения.  
  
## <a name="see-also"></a>См. также  
 [Новые возможности в API версии 1.2 подключаемого модуля системы управления версиями](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)


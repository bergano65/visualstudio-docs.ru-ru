---
title: Ликвидация файлов SAK Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0294198bb1560f8df6f17170013f88d4fe11e5cf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708501"
---
# <a name="elimination-of-sak-files"></a>Ликвидация файлов SAK
В Подключаемом API 1.2 файлы *sAK* были заменены флагами возможностей и новыми функциями, которые определяют, поддерживает ли плагин управления исходным управлением файл *MSSCCPRJ* и общие проверки.

## <a name="sak-files"></a>Файлы SAK
Visual Studio .NET 2003 создала временные файлы, прикреплённые к *sAK*. Эти файлы используются для определения поддержки плагина управления исходным элементом:

- Файл *MSSCCPRJ.SCC.*

- Несколько (общих) выездов.

Для плагинов, поддерживающих расширенные функции, предусмотренные в API 1.2 управления исходным управлением, IDE может обнаруживать эти возможности без создания временных файлов с помощью новых возможностей, флагов и функций, подробно описанных в следующих разделах.

## <a name="new-capability-flags"></a>Новые флаги возможностей
 `SCC_CAP_SCCFILE`

 `SCC_CAP_MULTICHECKOUT`

## <a name="new-functions"></a>Новые функции
- [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)

- [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)

 Если плагин управления исходным источником поддерживает несколько (общих) `SCC_CAP_MULTICHECKOUT` проверок, то `SccIsMultiCheckOutEnabled` он объявляет возможность и реализует функцию. Эта функция вызывается всякий раз, когда операция проверки происходит на любом из проектов, контролируемых исходным ресурсом.

 Если плагин управления исходным элементом поддерживает создание и использование файла *MSSCCPRJ.SCC,* то он объявляет `SCC_CAP_SCCFILE` возможность и реализует [SccWillCreateSccFile.](../../extensibility/sccwillcreatesccfile-function.md) Эта функция вызывается со списком файлов. Функция возвращается `TRUE' or 'FALSE` для каждого файла, чтобы указать, должна ли Visual Studio использовать для него файл *MSSCCPRJ.SCC.* Если плагин управления исходным элементом не поддерживает эти новые возможности и функции, он может использовать следующий ключ реестра, чтобы отключить создание этих файлов:

 **«HKEY_CURRENT_USER»Программное обеспечение»Microsoft,VisualStudio»8.0 (SourceControl) DoNotCreateTemporaryFilesInSourceControl** = *dword:00000001*

> [!NOTE]
> Если этот ключ реестра установлен на *dword:0000000000*, это эквивалентно ключу, который не существует, и Visual Studio все еще пытается создать временные файлы. Однако, если ключ реестра установлен на *dword:00000001*, Visual Studio не пытается создать временные файлы. Вместо этого он предполагает, что плагин управления исходным источником не поддерживает файл *MSSCCPRJ.SCC* и не поддерживает общие проверки.

## <a name="see-also"></a>См. также
- [Что нового в версии API-элемента управления исходным элементом](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

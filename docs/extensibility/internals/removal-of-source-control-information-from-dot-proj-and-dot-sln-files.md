---
title: Удаление сведений системы управления версиями из файлов proj и SLN
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 081766a8169ccc54888a076012b8281c485a20e5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318823"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Удаление сведений системы управления версиями из файлов PROJ и SLN
В версии 1.2 API подключаемых модулей управления источника SCC хранится в MSSCCPRJ. Файл SCC. Преимущество MSSCCPRJ. Файл SCC —, которое SCC сведения не исходные - контролируется, как в файлов proj и SLN.

## <a name="version-12-changes"></a>Изменения в версии 1.2
 В исходный элемент управления подключаемые модули, основанные на API подключаемых модулей управления исходной версии 1.1 сведения о системе управления версиями, хранится в проекта (.proj) и файлов решения (SLN). AuxPath указывается расположение базы данных сведений системы управления версиями, и конкретное расположение в базе данных задается ProjName. Это поведение может вызывать проблемы после ветви, разветвление или операций копирования, так как ProjName обычно будет недопустимым после любой из этих операций.

 В API подключаемых модулей управления исходной версии 1.1, интегрированной среды разработки используется ~ SAK-файлов для обнаружения, если подключаемый модуль поддерживается MSSCCPRJ. Метод SCC хранения информация системы управления версиями. API подключаемых модулей управления исходной версии 1.2 предоставляет новую возможность для обнаружения поддержка MSSCCPRJ. Файл SCC без использования ~ SAK-файл. Дополнительные сведения см. в разделе [Устранение ~ SAK-файлов](../../extensibility/internals/elimination-of-tilde-sak-files.md).

## <a name="see-also"></a>См. также
- [Новые возможности в API версии 1.2 подключаемого модуля системы управления версиями](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
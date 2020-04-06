---
title: Удаление информации о контроле исходного кода из файлов .proj и .sln
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba3085a7806bfb0556613d1fca1b94953dcdb0b2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705590"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Удаление сведений системы управления версиями из файлов PROJ и SLN
В версии 1.2 API управления исходным элементом информация SCC хранится в MSSCCPRJ. Файл SCC. Преимущество MSSCCPRJ. Файл SCC состоит в том, что информация SCC не контролируется источником, как в файлах .proj и .sln.

## <a name="version-12-changes"></a>Версия 1.2 Изменения
 В плагинах управления исходным элементом, основанных на версии API 1.1 управления исходным управлением, информация о контроле исходного кода хранится в файлах проекта (.proj) и solution (.sln). Местоположение базы данных информации управления исходным ресурсом указывается AuxPath, а конкретное местоположение в базе данных указывает ProjName. Такое поведение может вызвать проблемы после операций ветки, вилки или копирования, поскольку ProjName обычно будет недействительным после любой из этих операций.

 В версии API 1.1 Управления источника IDE использовал файлы SAK для обнаружения, поддерживает ли плагин MSSCCPRJ. Метод SCC для хранения информации о контроле источника. Версия API API управления исходным элементом обеспечивает новую возможность обнаружения поддержки MSSCCPRJ. Файл SCC без использования файла SAK. Для получения более [подробной информации см.](../../extensibility/internals/elimination-of-tilde-sak-files.md)

## <a name="see-also"></a>См. также
- [Новые возможности в API версии 1.2 подключаемого модуля системы управления версиями](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

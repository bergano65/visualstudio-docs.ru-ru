---
title: Справочник по API-интерфейсам профилировщика Visual Studio (машинный код)
description: Сведения об API-интерфейсах профилировщика Visual Studio, которые позволяют программно управлять объемом собранных данных и вставлять метки времени и профиля во время профилирования.
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, API
- Profiler, API
ms.assetid: a0c3be92-c263-4678-9fb9-bafead3bd5f5
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 46306697fb891dd7604cda193deaec087d164ad7
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2021
ms.locfileid: "98723157"
---
# <a name="visual-studio-profiler-api-reference-native"></a>Справочник по API-интерфейсам профилировщика Visual Studio (машинный код)
API-интерфейсы профилировщика Visual Studio позволяют программно управлять объемом собранных данных и вставлять метки времени и профиля во время профилирования. Чтобы использовать собственный API, включите файл заголовка *VSPerf.h* и добавьте файл *VSPerf.lib* в свой проект.

> [!NOTE]
> Сведения о пути к средствам профилирования см. в статье [Указание пути к программам командной строки средств профилирования](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

## <a name="in-this-section"></a>Содержание раздела
[CommentMarkAtProfile](../profiling/commentmarkatprofile.md)

[CommentMarkProfile](../profiling/commentmarkprofile.md)

[MarkProfile](../profiling/markprofile.md)

[NameProfile](../profiling/nameprofile.md)

[ResumeProfile](../profiling/resumeprofile.md)

[StartProfile](../profiling/startprofile.md)

[StopProfile](../profiling/stopprofile.md)

[SuspendProfile](../profiling/suspendprofile.md)

[PROFILE_CURRENTID](../profiling/profile-currentid.md)

## <a name="see-also"></a>См. также

- [Интерфейсы API средств профилирования](../profiling/profiling-tools-apis.md)
- [Пошаговое руководство. Использование API-интерфейсов профилировщика](../profiling/walkthrough-using-profiler-apis.md)

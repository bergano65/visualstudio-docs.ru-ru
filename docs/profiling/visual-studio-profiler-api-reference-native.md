---
title: Справочник по API-интерфейсам профилировщика Visual Studio (машинный код)
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
ms.workload:
- cplusplus
ms.openlocfilehash: 3f0071e98c9e36f3af11d318f480b4b9c6ec4cc1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62822824"
---
# <a name="visual-studio-profiler-api-reference-native"></a>Справочник по API-интерфейсам профилировщика Visual Studio (машинный код)
API-интерфейсы профилировщика Visual Studio позволяют программно управлять объемом собранных данных и вставлять метки времени и профиля во время профилирования. Чтобы использовать собственный API, включите файл заголовка *VSPerf.h* и добавьте файл *VSPerf.lib* в свой проект.

> [!NOTE]
> Сведения о пути к Средствам профилирования см. в статье [Указание пути к программам командной строки средств профилирования](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

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
- [Пошаговое руководство: использование API-интерфейсов профилировщика](../profiling/walkthrough-using-profiler-apis.md)

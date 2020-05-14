---
title: Обзор решений
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 767db749d953855cd5c6f81f356a195c830aa838
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705300"
---
# <a name="solutions-overview"></a>Обзор решений

Решение — это группировка одного или нескольких проектов, которые работают вместе для создания приложения. Информация о проекте и статусе, относящаяся к решению, хранится в двух разных файлах решения. [Файл решения (.sln)](solution-dot-sln-file.md) основан на тексте и может быть помещен под управление исходного кода и совместно между пользователями. [Пользовательский вариант решения (.suo) файл](solution-user-options-dot-suo-file.md) является двоичным. В результате файл .suo не может быть помещен под управление исходного кода и содержит информацию о конкретной пользовательской информации.

Любой VSPackage может написать на любой тип файла решения. Из-за характера файлов, Есть два различных интерфейсов реализованы, чтобы написать им. Интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> записывает текстовую информацию в <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> файл .sln, а интерфейс записывает двоичные потоки в файл .suo.

> [!NOTE]
> Проект не должен явно записывать запись для себя в файл решения; окружающая среда обрабатывает это для проекта. Поэтому, если вы не хотите добавить дополнительный контент специально в файл решения, вам не нужно регистрировать ваш VSPackage таким образом.

Каждый упорство решения поддержки VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> использует три интерфейса, интерфейс, который реализуется `IVsPersistSolutionProps` `IVsPersistSolutionOpts`средой и называется VSPackage, и , которые оба реализованы VSPackage. Интерфейс `IVsPersistSolutionOpts` должен быть реализован только для того, чтобы конфиденциальная информация была написана VSPackage в файл .suo.

При открытии решения происходит следующий процесс.

1. Окружающая среда считывает решение.

2. Если среда `CLSID`находит, она загружает соответствующий VSPackage.

3. Если VSPackage загружен, среда требует `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> интерфейса для интерфейса, который требуется VSPackage.

   - При чтении из файла .sln среда требует `QueryInterface` `IVsPersistSolutionProps`.

   - При чтении из файла .suo, среда требует `QueryInterface` . `IVsPersistSolutionOpts`

   Конкретную информацию, касающуюся использования этих файлов, можно найти в [solution (. Sln) Параметры](../../extensibility/internals/solution-dot-sln-file.md) пользователя файлов и [решений (. Suo) Файл](../../extensibility/internals/solution-user-options-dot-suo-file.md).

> [!NOTE]
> Если требуется создать новую конфигурацию решений, состоящую из конфигураций двух проектов и исключающей третью из сборки, необходимо использовать uI-и., или автоматизацию страниц свойств. Вы не можете изменить конфигурацию диспетчера сборки решений непосредственно, но вы можете `SolutionBuild` манипулировать менеджером сборки решений, используя класс от DTE в модели автоматизации. Для получения дополнительной информации о настройке решений [см.](../../extensibility/internals/solution-configuration.md)

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>

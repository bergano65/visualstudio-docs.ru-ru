---
title: Общие сведения о решениях
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fe348d3e6b5c896ff4c76965b918d41dfe00328
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62859332"
---
# <a name="solutions-overview"></a>Общие сведения о решениях

Решение — это группа из одного или нескольких проектов, работающих совместно для создания приложения. Проект и состояние сведения, относящиеся к решению, хранятся в двух файлах другого решения. [Файл решения (SLN)](solution-dot-sln-file.md) основана на тексте и может быть помещен в систему управления версиями и совместно использоваться пользователями. [Файл параметров (.suo) решение пользователя](solution-user-options-dot-suo-file.md) двоичных данных. В результате SUO-файл нельзя поместить в систему управления версиями и содержит сведения о пользователе.

Любой пакет VSPackage можно написать для любого типа файла решения. Из-за природы файлы существует два разных интерфейсов, реализованных для записи к ним. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> Интерфейс записывает текстовые данные в SLN-файл и <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> интерфейс записывает двоичные потоки SUO-файл.

> [!NOTE]
> Проект не нужно явно добавить запись для себя в файл решения; Эти задачи выполняет среда, для проекта. Таким образом только если вы хотите добавить дополнительное содержимое в частности к файлу решения, вы не обязательно должны зарегистрировать VSPackage таким образом.

Каждый пакет VSPackage, поддержка сохраняемости решения использует три интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> интерфейс, который реализуется средой и вызвана VSPackage, и `IVsPersistSolutionProps` и `IVsPersistSolutionOpts`, осуществляют такие попытки при оба реализованы по VSPackage. `IVsPersistSolutionOpts` Интерфейс только должна быть реализована при конфиденциальную информацию для записи с VSPackage SUO-файл.

При открытии решения, процесс выполняется.

1. Среде считывает решения.

2. Обнаружив среде `CLSID`, он загружает соответствующий пакет VSPackage.

3. Если VSPackage загружается, среда вызывает метод `QueryInterface` для <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> интерфейса для интерфейса, который требует VSPackage.

   - При чтении из SLN-файла, среда вызывает `QueryInterface` для `IVsPersistSolutionProps`.

   - При чтении из файла .suo, среда вызывает `QueryInterface` для `IVsPersistSolutionOpts`.

   Определенные сведения, относящиеся к использованию этих файлов можно найти в [решение (. Файл SLN)](../../extensibility/internals/solution-dot-sln-file.md) и [пользовательских параметров решения (. SUO-) файл](../../extensibility/internals/solution-user-options-dot-suo-file.md).

> [!NOTE]
> Если вы хотите создать новую конфигурацию решения, состоящий из двух проектов конфигураций и исключение в третьем из сборки, необходимо использовать пользовательский Интерфейс страницы свойств или автоматизации. Нельзя изменить диспетчер конфигураций построения решения и их свойств напрямую, но можно управлять с помощью диспетчер построения решения `SolutionBuild` от DTE класса в модели автоматизации. Дополнительные сведения о настройке решения, см. в разделе [конфигурации решения](../../extensibility/internals/solution-configuration.md).

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
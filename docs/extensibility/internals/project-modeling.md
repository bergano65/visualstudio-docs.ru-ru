---
title: Моделирование проектов Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1ac89baf5bc7582d3430532938a5e5a0c35a4c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706552"
---
# <a name="project-modeling"></a>Моделирование проекта
Следующим шагом в обеспечении автоматизации вашего проекта является <xref:EnvDTE.Projects> `ProjectItems` реализация стандартных объектов проекта: и коллекций; и `Project` <xref:EnvDTE.ProjectItem> объектов; а остальные объекты, уникальные для вашей реализации. Эти стандартные объекты определены в файле Dteinternal.h. Реализация стандартных объектов предусмотрена в образце BscPrj. Эти классы можно использовать в качестве моделей для создания собственных стандартных объектов проекта, которые стоят бок о бок с объектами проекта из других типов проектов.

 Потребитель автоматизации предполагает возможность звонить <xref:EnvDTE.Solution>`<UniqueProjName>")` (" <xref:EnvDTE.ProjectItems> `n`и ( ) где n является индексным номером для получения конкретного проекта в решении. Создание этого вызова автоматизации <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> заставляет среду вызывать соответствующую иерархию проекта, передавая VSITEMID_ROOT в качестве параметра ItemID и VSHPROPID_ExtObject в качестве параметра VSHPROPID. `IVsHierarchy::GetProperty``IDispatch` возвращает указатель на объект автоматизации, обеспечивающий основной `Project` интерфейс, который вы реализовали.

 Ниже приводится синтаксис `IVsHierarchy::GetProperty`.

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`,

 `VSHPROPID` `propid`,

 `VARIANT` `*pvar`

 `);`

 Проекты размещают вложения и используют коллекции для создания групп элементов проекта. Иерархия выглядит следующим образом.

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 Вложение означает, <xref:EnvDTE.ProjectItem> что <xref:EnvDTE.ProjectItems> объект может быть `ProjectItems` собран одновременно, поскольку коллекция может содержать вложенные объекты. Пример Базового проекта не демонстрирует это вложение. Реализуя `Project` объект, вы участвуете в древовидной структуре, характеризующей дизайн общей модели автоматизации.

 Автоматизация проекта следует по следующему пути на следующей диаграмме.

 ![Объекты проекта Visual Studio](../../extensibility/internals/media/projectobjects.gif "ПроектОбъекты") Автоматизация проекта

 Если объект не `Project` реализуется, среда по-прежнему `Project` возвращает общий объект, содержащий только название проекта.

## <a name="see-also"></a>См. также
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>

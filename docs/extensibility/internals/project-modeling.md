---
title: Моделирование проекта | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 42e810a36478e49a578c6713d20f1bfc6be98309
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725562"
---
# <a name="project-modeling"></a>Моделирование проекта
Следующим шагом в предоставлении автоматизации для проекта является реализация стандартных объектов проекта: <xref:EnvDTE.Projects> и `ProjectItems` Collections; объекты `Project` и <xref:EnvDTE.ProjectItem>; и оставшиеся объекты, уникальные для вашей реализации. Эти стандартные объекты определены в файле Дтеинтернал. h. Реализация стандартных объектов представлена в примере Бскпрж. Эти классы можно использовать в качестве моделей для создания собственных объектов стандартных проектов, которые будут изолированы параллельно с объектами проекта из других типов проектов.

 Потребитель автоматизации предполагает возможность вызова <xref:EnvDTE.Solution> ("`<UniqueProjName>")` и <xref:EnvDTE.ProjectItems> (`n`), где n — номер индекса для получения конкретного проекта в решении. В результате этого вызова службы автоматизации среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> в соответствующей иерархии проекта, передавая VSITEMID_ROOT в качестве параметра ItemID и VSHPROPID_ExtObject в качестве параметра ВШПРОПИД. `IVsHierarchy::GetProperty` возвращает указатель `IDispatch` на объект автоматизации, предоставляющий реализуемый базовый интерфейс `Project`.

 Ниже приведен синтаксис `IVsHierarchy::GetProperty`.

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`

 `VSHPROPID` `propid`

 `VARIANT` `*pvar`

 `);`

 Проекты, предназначенные для вложенности и использования коллекций для создания групп элементов проекта. Иерархия выглядит следующим образом.

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 Вложение означает, что объект <xref:EnvDTE.ProjectItem> может быть <xref:EnvDTE.ProjectItems> коллекции одновременно, так как коллекция `ProjectItems` может содержать вложенные объекты. Пример базового проекта не демонстрирует такое вложение. Реализуя объект `Project`, вы участвуете в древовидной структуре, которая характеризует структуру общей модели автоматизации.

 Автоматизация проекта соответствует пути на следующей схеме.

 ![Объекты проектов Visual Studio](../../extensibility/internals/media/projectobjects.gif "прожектобжектс") Автоматизация проектов

 Если объект `Project` не реализован, среда по-прежнему будет возвращать универсальный объект `Project`, содержащий только имя проекта.

## <a name="see-also"></a>См. также
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>
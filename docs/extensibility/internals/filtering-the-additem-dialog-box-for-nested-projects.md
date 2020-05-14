---
title: Фильтрация ящика Диагностика AddItem для вложенных проектов (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2bc97b6041f4844ff71fe1d38a7103e1219888be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708384"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>Фильтр овоедело диалога AddItem для вложенных проектов
При отображении диалогового окна **AddItem** для вложенного проекта родительский проект может контролировать элементы, отображаемые в диалоговом поле.

 Интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> позволяет фильтровать узлы, которые будут находиться в диалоговом окне **AddItem.** Когда проект «ребенок» отображает диалоговую коробку **AddItem,** родитель может реализовать элементы `IVsFilterAddProjectItemDlg` интерфейса и фильтрации, которые в противном случае были бы отображены в проекте ребенка.

 Когда проекты группируются по функциям по `IVsFilterAddProjectItemDlg` определенным родительским проектам, можно реализовать, когда пользователь выбирает **Элемент добавления в** меню ярлыка в вложенном проекте. Реализация `IvsFilterAddProjectItemDlg displays` только элементов проекта или файлов, специфиченных для этой группы. Элементы проекта для других групп отфильтровываются из окна диалога, даже если они хранятся в том же каталоге.

 Когда пользователь открывает диалоговую коробку **AddItem** для ребенка, `IVsFilterAddProjectItemDlg` требуется реализация интерфейса родительского проекта.

 Интерфейс `IVsFilterAddProjectItemDlg` также может осуществлять фильтрацию по категориям. Для получения дополнительной информации [Register project and item templates](../../extensibility/internals/registering-project-and-item-templates.md)см. [Add items to the Add New Item dialog box](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Добавление элементов в диалоговую окно Добавить новый элемент](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)
- [Проекты гнезда](../../extensibility/internals/nesting-projects.md)

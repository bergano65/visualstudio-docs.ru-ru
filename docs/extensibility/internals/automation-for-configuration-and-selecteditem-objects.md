---
title: Автоматизация для конфигурации и выбранных объектов пункта (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0341cdf56b32b8b1ac77104b3f3e813ae0610767
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709974"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Автоматизация для объектов конфигурации и SelectedItem

Вы можете автоматизировать процессы сборки и выбранных элементов в Visual Studio.

## <a name="automation-for-builds"></a>Автоматизация для сборок

Сборка или конфигурация имеет модель автоматизации, которая предоставляется при реализации. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> Дополнительные сведения см. в статье [Общие сведения о конфигурациях сборок](../../ide/understanding-build-configurations.md).

Если вы создаете VSPackage и хотите управлять вариантами конфигурации, необходимо использовать модель автоматизации.

## <a name="automation-for-selecteditem"></a>Автоматизация для SelectedItem

Вы не должны предоставлять реализацию `SelectedItem` для объекта, потому что Visual Studio содержит стандартную реализацию. Тем не менее, `SelectedItem` вы можете реализовать объект, если вы предпочитаете. Необходимо реализовать объект, содержащий `SelectedItem` интерфейс, и вернуть ответ <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> на `VSITEMID` вызов в метод с набором [для __VSHPROPID. VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>).

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [Внести свой вклад в модель автоматизации](../../extensibility/internals/contributing-to-the-automation-model.md)
- [Общие сведения о конфигурациях сборок](../../ide/understanding-build-configurations.md)

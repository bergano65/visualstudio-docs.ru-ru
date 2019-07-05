---
title: Модель автоматизации для объектов конфигурации и SelectedItem | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6c9dc8012433f9ec73f15b9249f6b7ac08bdad7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347974"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Автоматизация для объектов конфигурации и SelectedItem

Вы можете автоматизировать сборку и процессов выбранного элемента в Visual Studio.

## <a name="automation-for-builds"></a>Автоматизация сборки

Сборки или конфигурации имеет модель автоматизации, которая предоставляется при реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>. Дополнительные сведения см. в статье [Общие сведения о конфигурациях сборок](../../ide/understanding-build-configurations.md).

Если вы создаете VSPackage и хотите контролировать параметры конфигурации, необходимо использовать модель автоматизации.

## <a name="automation-for-selecteditem"></a>Модель автоматизации для SelectedItem

Необходимо обеспечить реализацию для `SelectedItem` объекта, так как Visual Studio содержит стандартную реализацию. Тем не менее, можно реализовать `SelectedItem` объекта, если вы предпочитаете. Необходимо реализовать объект, содержащий `SelectedItem` интерфейс и возврат ответа на вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> метод с `VSITEMID` присвоено [__VSHPROPID. VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>).

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [Участие в модели автоматизации](../../extensibility/internals/contributing-to-the-automation-model.md)
- [Общие сведения о конфигурациях построения](../../ide/understanding-build-configurations.md)
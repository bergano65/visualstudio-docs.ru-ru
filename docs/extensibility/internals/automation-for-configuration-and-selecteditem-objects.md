---
title: Автоматизация для объектов Configuration и SelectedItem | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709974"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Автоматизация для объектов Configuration и SelectedItem

В Visual Studio можно автоматизировать процесс сборки и выбора элементов.

## <a name="automation-for-builds"></a>Автоматизация для сборок

Сборка или конфигурация имеет модель автоматизации, предоставляемую при реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> . Дополнительные сведения см. в статье [Общие сведения о конфигурациях сборок](../../ide/understanding-build-configurations.md).

Если вы создаете VSPackage и хотите управлять параметрами конфигурации, необходимо использовать модель автоматизации.

## <a name="automation-for-selecteditem"></a>Автоматизация для SelectedItem

Нет необходимости предоставлять реализацию для `SelectedItem` объекта, так как Visual Studio содержит стандартную реализацию. Однако при желании можно реализовать `SelectedItem` объект. Необходимо реализовать объект, содержащий `SelectedItem` интерфейс, и вернуть ответ на вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> метода с параметром `VSITEMID` [__VSHPROPID. VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>).

## <a name="see-also"></a>См. также раздел

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [Участие в модели автоматизации](../../extensibility/internals/contributing-to-the-automation-model.md)
- [Общие сведения о конфигурациях построения](../../ide/understanding-build-configurations.md)

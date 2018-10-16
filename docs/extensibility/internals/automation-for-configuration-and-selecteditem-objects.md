---
title: Модель автоматизации для объектов конфигурации и SelectedItem | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4a1c745ad8f40ac755513f49db7b522f83f075a8
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500736"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Автоматизация для объектов конфигурации и SelectedItem
Можно автоматизировать сборки и процессы выбранного элемента в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="automation-for-builds"></a>Автоматизация сборки  
 Сборки или конфигурации имеет модель автоматизации, которая предоставляется при реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>. Дополнительные сведения см. в статье [Общие сведения о конфигурациях сборок](../../ide/understanding-build-configurations.md).  
  
 Если вы создаете VSPackage и хотите контролировать параметры конфигурации, необходимо использовать модель автоматизации.  
  
## <a name="automation-for-selecteditem"></a>Модель автоматизации для SelectedItem  
 Необходимо обеспечить реализацию для `SelectedItem` объекта, так как Visual Studio содержит стандартную реализацию. Тем не менее, можно реализовать `SelectedItem` объекта, если вы предпочитаете. Необходимо реализовать объект, содержащий `SelectedItem` интерфейс и возврат ответа на вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> метод с `VSITEMID` присвоено <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Участие в модели автоматизации](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [Общие сведения о конфигурациях построения](../../ide/understanding-build-configurations.md)
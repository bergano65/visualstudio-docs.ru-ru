---
title: Модель автоматизации для объектов конфигурации и SelectedItem | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60efbb25b0b5b52e1392ce84c16710a78dde7b16
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54919282"
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
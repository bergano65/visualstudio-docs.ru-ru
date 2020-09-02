---
title: Автоматизация для объектов Configuration и SelectedItem | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42faf8127c1ab70d3470aa497a0cdab6058060f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157260"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Автоматизация для объектов конфигурации и SelectedItem
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Можно автоматизировать сборку и выбранные процессы элементов в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="automation-for-builds"></a>Автоматизация для сборок  
 Сборка или конфигурация имеет модель автоматизации, предоставляемую при реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> . Дополнительные сведения см. в разделе [Общие сведения о конфигурациях построения](../../ide/understanding-build-configurations.md).  
  
 Если вы создаете VSPackage и хотите управлять параметрами конфигурации, необходимо использовать модель автоматизации.  
  
## <a name="automation-for-selecteditem"></a>Автоматизация для SelectedItem  
 Нет необходимости предоставлять реализацию для `SelectedItem` объекта, так как Visual Studio содержит стандартную реализацию. Однако при желании можно реализовать `SelectedItem` объект. Необходимо реализовать объект, содержащий `SelectedItem` интерфейс, и вернуть ответ на вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> метода с ПАРАМЕТРом вситемид, имеющим значение <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> .  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Вклад в модель автоматизации](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [Основные сведения о конфигурациях сборки](../../ide/understanding-build-configurations.md)

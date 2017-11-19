---
title: "Модель автоматизации для настроек и объектов SelectedItem | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 42a3b8bdd8930c9006ba49fd0f2e2dd2491b38cb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Модель автоматизации для настроек и объектов SelectedItem
Можно автоматизировать сборки и процессы выбранного элемента в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="automation-for-builds"></a>Автоматизация для сборок  
 Сборки или конфигурации имеет модель автоматизации, которая предоставляется при реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>. Дополнительные сведения см. в разделе [Общие сведения о конфигурациях построения](../../ide/understanding-build-configurations.md).  
  
 Если создать пакет VSPackage, чтобы контролировать параметры конфигурации необходимо использовать модель автоматизации.  
  
## <a name="automation-for-selecteditem"></a>Модель автоматизации для SelectedItem  
 Необходимо предоставить реализацию `SelectedItem` объекта, так как Visual Studio содержит стандартную реализацию. Тем не менее, можно реализовать `SelectedItem` объекта, если вы предпочитаете. Необходимо реализовать объект, содержащий `SelectedItem` интерфейса и возвращает ответ на вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> метод с VSITEMID <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Дополнение к модели автоматизации](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [Общие сведения о конфигурациях построения](../../ide/understanding-build-configurations.md)
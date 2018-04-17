---
title: Что&#39;новые возможности системы управления версиями | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b46730ab1acac6605af2e1ff1c418dbe8c886406
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="what39s-new-in-source-control"></a>Что&#39;новые возможности системы управления версиями
В [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] может обеспечить решение управления глубокий уровень интеграции источника, реализовав VSPackage системы управления версиями. В этом разделе описаны возможности системы управления версиями пакетов VSPackage и общие сведения о реализации действий.  
  
## <a name="the-source-control-vspackage"></a>VSPackage управления источника  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] поддерживает два типа исходного решения для управления. Во всех версиях [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], можно интегрировать на основе API подключаемых модулей для управления источника подключаемого модуля. Можно также создать пакет VSPackage для системы управления версиями, которая предоставляет прямой интеграции [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] подходит для решения для управления источника, которые требуется высокий уровень квалификации и автономность.  
  
 VSPackage может добавлять практически любые функциональные возможности для [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Элемент управления источником VSPackage предоставляет полный исходный элемент управления [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], из пользовательского интерфейса, которые отображаются для пользователя, для обмена данными между серверную систему управления версиями.  
  
 Реализация системы управления версиями VSPackage необходима стратегия «все или ничего». Создатель VSPackage системы управления версиями необходимо приобрести значительный объем усилий в реализации интерфейсов управления источника и новые элементы пользовательского интерфейса (диалоговые окна, меню и панелей инструментов) для покрытия всей системы управления версиями, а также интерфейсы требуется для любого пакета успешно интегрировать [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Следующие шаги предоставляют общие сведения о том, что необходимо для реализации пакет системы управления версиями. Дополнительные сведения см. в разделе [создания пакетов VSPackage управления источника](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
1.  Создайте пакет VSPackage, который proffers в систему управления версиями закрытый.  
  
2.  Реализовывать интерфейсы, связанные с управлением служб источника, которые являются предлагаемых [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (например, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> интерфейс).  
  
3.  Зарегистрируйте VSPackage системы управления версиями.  
  
4.  Реализуйте все системы управления версиями пользовательского интерфейса, включая элементы меню, диалоговые окна, панели инструментов и контекстные меню.  
  
5.  Все события источника связанные с управлением передаются VSackage системы управления версиями при активной и должны обрабатываться VSPackage.  
  
6.  Системы управления версиями VSPackage должен прослушивать для событий, например реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> интерфейс, а также события отслеживания проекта документа (TPD) (как это реализовано <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> интерфейса) и выполните необходимые действия.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Обзор](../../extensibility/internals/source-control-integration-overview.md)   
 [Создание пакета VSPackage системы управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md)
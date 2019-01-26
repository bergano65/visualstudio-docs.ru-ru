---
title: Что&#39;возможности системы управления версиями | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b0eb0d88d0e4cf2628ef2c9c8ed2c9070f25aac9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55004777"
---
# <a name="what39s-new-in-source-control"></a>Что&#39;возможности системы управления версиями
В [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] может обеспечить решение управления интегрирована источника путем реализации пакета VSPackage системы управления версиями. В этом разделе описаны возможности системы управления версиями пакетов VSPackage и общие сведения о реализации действий.  
  
## <a name="the-source-control-vspackage"></a>Пакет VSPackage управления версиями  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] поддерживает два типа решений управления версиями. Во всех версиях [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], по-прежнему можно интегрировать, основанная на API подключаемых модулей управления источника подключаемого модуля. Вы также можете создать VSPackage для системы управления версиями, который предоставляет глубокого интеграции [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] подходит для решений управления версиями, для которых требуется высокий уровень квалификации и независимость.  
  
 VSPackage может добавлять практически любые функциональные возможности для [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Пакет VSPackage системы управления версиями обеспечивает средства управления полный исходный для [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], с помощью пользовательского интерфейса, представленные пользователю обмена данными между серверной части с системой управления версиями.  
  
 Для реализации пакета VSPackage системы управления версиями требуется стратегию «все или ничего». Создатель пакета VSPackage системы управления версиями необходимо инвестировать значительный объем трудозатрат на применение нескольких интерфейсов управления источника и новых элементов пользовательского интерфейса (диалоговые окна, меню и панелей инструментов) для охвата всей системы управления версиями, а также интерфейсы требуется для успешной интеграции с любой пакет [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Следующие действия предоставляют общие сведения о необходимых для реализации пакет системы управления версиями. Дополнительные сведения см. в разделе [Создание пакета VSPackage управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
1. Создайте пакет VSPackage, который предоставляет определенную службу частного исходного элемента управления.  
  
2. Реализовывать интерфейсы в связанные с управлением версиями службы источника, которые являются предлагаемых [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (например, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> интерфейс).  
  
3. Регистрация пакета VSPackage системы управления версиями.  
  
4. Реализуйте все системы управления версиями пользовательского интерфейса, включая элементы меню, диалоговых окон, панелей инструментов и контекстные меню.  
  
5. Все источника события, связанные с управлением версиями передаются VSackage системы управления версиями, когда он активен и должны обрабатываться VSPackage.  
  
6. Пакет VSPackage системы управления версиями необходимо прослушивать событий, например реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> интерфейс, а также события отслеживания проекта документа (TPD) (как реализованный <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> интерфейс) и выполните необходимые действия.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Обзор](../../extensibility/internals/source-control-integration-overview.md)   
 [Создание пакета VSPackage системы управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md)
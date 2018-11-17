---
title: Что&#39;возможности системы управления версиями | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9a108acb2ae32b64292cd819c75de4726f067a00
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752458"
---
# <a name="what39s-new-in-source-control"></a>Что&#39;возможности системы управления версиями
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] может обеспечить решение управления интегрирована источника путем реализации пакета VSPackage системы управления версиями. В этом разделе описаны возможности системы управления версиями пакетов VSPackage и общие сведения о реализации действий.  
  
## <a name="the-source-control-vspackage"></a>Пакет VSPackage управления версиями  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] поддерживает два типа решений управления версиями. Во всех версиях [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], по-прежнему можно интегрировать, основанная на API подключаемых модулей управления источника подключаемого модуля. Вы также можете создать VSPackage для системы управления версиями, который предоставляет глубокого интеграции [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] подходит для решений управления версиями, для которых требуется высокий уровень квалификации и независимость.  
  
 VSPackage может добавлять практически любые функциональные возможности для [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Пакет VSPackage системы управления версиями обеспечивает средства управления полный исходный для [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], с помощью пользовательского интерфейса, представленные пользователю обмена данными между серверной части с системой управления версиями.  
  
 Для реализации пакета VSPackage системы управления версиями требуется стратегию «все или ничего». Создатель пакета VSPackage системы управления версиями необходимо инвестировать значительный объем трудозатрат на применение нескольких интерфейсов управления источника и новых элементов пользовательского интерфейса (диалоговые окна, меню и панелей инструментов) для охвата всей системы управления версиями, а также интерфейсы требуется для успешной интеграции с любой пакет [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Следующие действия предоставляют общие сведения о необходимых для реализации пакет системы управления версиями. Дополнительные сведения см. в разделе [Создание пакета VSPackage управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
1.  Создайте пакет VSPackage, который предоставляет определенную службу частного исходного элемента управления.  
  
2.  Реализовывать интерфейсы в связанные с управлением версиями службы источника, которые являются предлагаемых [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (например, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> интерфейс).  
  
3.  Регистрация пакета VSPackage системы управления версиями.  
  
4.  Реализуйте все системы управления версиями пользовательского интерфейса, включая элементы меню, диалоговых окон, панелей инструментов и контекстные меню.  
  
5.  Все источника события, связанные с управлением версиями передаются VSackage системы управления версиями, когда он активен и должны обрабатываться VSPackage.  
  
6.  Пакет VSPackage системы управления версиями необходимо прослушивать событий, например реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> интерфейс, а также события отслеживания проекта документа (TPD) (как реализованный <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> интерфейс) и выполните необходимые действия.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Обзор](../../extensibility/internals/source-control-integration-overview.md)   
 [Создание пакета VSPackage системы управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md)


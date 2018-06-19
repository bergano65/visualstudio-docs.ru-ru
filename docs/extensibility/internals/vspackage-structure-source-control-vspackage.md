---
title: Структура пакета VSPackage (VSPackage управления источника) | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 13b811b504259bf10440419b3cb4029a4c239c5e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142793"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Структура пакета VSPackage (VSPackage управления источника)
Пакет SDK управления источника предоставляет рекомендации по созданию пакетов VSPackage, который позволяет разработчику элемента управления источника интегрировать его или ее функций системы управления версиями с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] среды. VSPackage — это компонент COM, который обычно загружается по запросу [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE) на основе служб, объявленные в пакете, в реестр. Каждый пакет VSPackage должен реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. VSPackage обычно занимают услугах, предлагаемых [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки и proffers некоторые службы.  
  
 VSPackage объявляет элементами меню и устанавливает состояние элемента по умолчанию через vsct-файле. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Интегрированная среда разработки отображает пункты меню в этом состоянии до окончания загрузки VSPackage. Следовательно, реализацию VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод вызывается для включения или отключения пунктов меню.  
  
## <a name="source-control-package-characteristics"></a>Параметры пакета управления источника  
 Системы управления версиями, VSPackage тесно интегрирована в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Семантика VSPackage включают:  
  
-   Интерфейс, реализуемый посредством выполняется пакет VSPackage ( `IVsPackage` интерфейса)  
  
-   Реализация команды пользовательского интерфейса (vsct-файл и реализацию <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейса)  
  
-   Регистрация VSPackage с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Системы управления версиями VSPackage должны обмениваться данными с этими других [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] сущностей:  
  
-   Проекты  
  
-   Редакторы  
  
-   Решения  
  
-   Windows  
  
-   Запущенной таблице документов  
  
### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Службы среды Visual Studio, которые могут быть использованы  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 Служба SVsRegisterScciProvider  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### <a name="vsip-interfaces-implemented-and-called"></a>Интерфейсы VSIP реализованы и вызывается  
 Пакет системы управления версиями является VSPackage, и поэтому он может взаимодействовать непосредственно с других пакетов VSPackage, которые зарегистрированы в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Чтобы обеспечить полный спектр функций системы управления версиями, системы управления версиями VSPackage может обрабатывать интерфейсы, предоставляемые проектов или оболочки.  
  
 Каждый проект в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] необходимо реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> распознается как проект в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки. Тем не менее, этот интерфейс не является специальным недостаточно для системы управления версиями. Проекты, которые должны находиться под узлом источника управлять реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>. Этот интерфейс используется системой управления версиями VSPackage для запроса проект для его содержимого и предоставить его глифы и данные привязки (сведения, необходимые для установления соединения между расположением сервера и проекта, который находится в папке на диске Система управления версиями).  
  
 Система управления версиями VSPackage реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, который в свою очередь позволяет проекты регистрироваться для системы управления версиями и извлекать их переноса состояния.  
  
 Полный список интерфейсов, которые необходимо принимать во внимание VSPackage системы управления версиями см. в разделе [связанных служб и интерфейсов](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).  
  
## <a name="see-also"></a>См. также  
 [Элементы макета](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [Связанные службы и интерфейсы](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
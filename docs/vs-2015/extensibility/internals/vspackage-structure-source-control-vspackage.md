---
title: Структура VSPackage (пакет VSPackage системы управления версиями) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 08bb0a296daca0de1c02b905a75fb10ce05f254e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205997"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Структура VSPackage (пакет VSPackage системы управления версиями)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Пакет SDK пакета системы управления версиями содержит рекомендации по созданию VSPackage, позволяющему разработчику системы управления версиями интегрировать свои функции управления версиями в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] среду. VSPackage — это COM-компонент, который обычно загружается по запросу [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] интегрированной средой разработки (IDE) на основе служб, объявленных пакетом в записях реестра. Каждый пакет VSPackage должен реализовывать <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> . Пакет VSPackage обычно использует службы, предлагаемые [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] интегрированной средой разработки, и профферс некоторые службы.  
  
 Пакет VSPackage объявляет свои пункты меню и устанавливает состояние элемента по умолчанию с помощью файла. vsct. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Интегрированная среда разработки отображает пункты меню в этом состоянии до тех пор, пока не будет загружен пакет VSPackage. Затем <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> для включения или отключения пунктов меню вызывается реализация метода VSPackage.  
  
## <a name="source-control-package-characteristics"></a>Характеристики пакета системы управления версиями  
 Пакет VSPackage для системы управления версиями тесно интегрирован в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 Семантика VSPackage включает в себя следующее:  
  
- Интерфейс, который должен быть реализован с помощью VSPackage ( `IVsPackage` интерфейс)  
  
- Реализация команд пользовательского интерфейса (vsct-файл и реализация <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейса)  
  
- Регистрация пакета VSPackage с помощью [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
  Пакет VSPackage системы управления версиями должен взаимодействовать с этими другими [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] сущностями:  
  
- Проекты  
  
- Редакторы  
  
- Решения  
  
- Windows  
  
- Таблица выполняющегося документа  
  
### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Службы среды Visual Studio, которые могут быть использованы  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 Служба СвсрегистерскЦипровидер  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### <a name="vsip-interfaces-implemented-and-called"></a>Реализованные и вызываемые интерфейсы VSIP  
 Пакет управления версиями является VSPackage и поэтому может взаимодействовать напрямую с другими пакетами VSPackage, зарегистрированными в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Чтобы обеспечить полный спектр функций управления версиями, пакет VSPackage системы управления версиями может работать с интерфейсами, предоставляемыми проектами или оболочкой.  
  
 Каждый проект в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] должен реализовывать, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> чтобы быть распознанным как проект в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] интегрированной среде разработки. Однако этот интерфейс не является достаточно специализированным для системы управления версиями. Проекты, которые должны находиться в системе управления версиями, реализуют <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> . Этот интерфейс используется пакетом VSPackage системы управления версиями для запроса содержимого проекта и предоставления ему глифов и сведений о привязке (сведения, необходимые для установления соединения между расположением сервера и расположением на диске проекта, который находится в системе управления версиями).  
  
 Пакет VSPackage системы управления версиями реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> , который, в свою очередь, позволяет проектам регистрировать себя для системы управления версиями и извлекать их глифы состояния.  
  
 Полный список интерфейсов, которые должен учитывать пакет VSPackage системы управления версиями, см. в разделе [связанные службы и интерфейсы](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы дизайна](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [Связанные службы и интерфейсы](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

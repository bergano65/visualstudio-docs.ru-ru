---
title: Структура VSPackage (пакет VSPackage управления версиями) | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8c27eb3c0bc977f716d3437042e1e4105eb1692d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557769"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Структура VSPackage (пакет VSPackage системы управления версиями)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [структура VSPackage (пакет VSPackage управления версиями)](https://docs.microsoft.com/visualstudio/extensibility/internals/vspackage-structure-source-control-vspackage).  
  
Пакет SDK для пакета управления для источника предоставляет рекомендации по созданию пакетов VSPackage, который позволяет разработчику элемента управления источника интегрировать свой функции системы управления версиями с [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] среды. VSPackage — это компонент COM, который загружается по запросу обычно [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] интегрированной среды разработки (IDE) на основе служб, которые объявляются с помощью пакета в записи в реестр. Каждый пакет VSPackage должен реализовывать <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. VSPackage обычно потребляет служб, предоставляемых [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] интегрированной среды разработки и предлагает некоторые службы.  
  
 VSPackage объявляет элементами меню и устанавливает состояние элемента по умолчанию с помощью файла .vsct. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Среда интегрированной разработки отобразит пункты меню в этом состоянии до загрузки VSPackage. Как следствие, реализацию VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод вызывается для включения или отключения пунктов меню.  
  
## <a name="source-control-package-characteristics"></a>Характеристик пакета управления источника  
 VSPackage является тесная интеграция системы управления версиями [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Семантика VSPackage включают:  
  
-   Интерфейс, реализуемый размещению VSPackage ( `IVsPackage` интерфейс)  
  
-   Реализация команды пользовательского интерфейса (vsct-файл и реализации <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс)  
  
-   Регистрация пакета VSPackage с [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Пакет VSPackage системы управления версиями должны взаимодействовать с этими других [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] сущностей:  
  
-   Проекты  
  
-   Редакторы  
  
-   Решения  
  
-   Windows  
  
-   В таблице выполняющихся документов  
  
### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Службы среды Visual Studio, которые могут включать  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 Служба SVsRegisterScciProvider  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### <a name="vsip-interfaces-implemented-and-called"></a>VSIP интерфейсы реализованы и вызывается  
 Пакет системы управления версиями является VSPackage, и поэтому она может напрямую взаимодействовать с других пакетов VSPackage, должны быть зарегистрированы с помощью [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Чтобы обеспечить доступ ко всем возможностям функции системы управления версиями, системы управления версиями VSPackage могут работать с интерфейсов, предоставляемых платформой проектов или оболочки.  
  
 Каждый проект в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] должен реализовывать <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> распознается как проект внутри [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] интегрированной среды разработки. Тем не менее, этот интерфейс не является специальным достаточно для системы управления версиями. Проекты, которые должны быть под источником управления реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>. Этот интерфейс используется системой управления версиями VSPackage для запроса проекта за их содержимое и предоставлять его глифы и сведения о привязке (сведения, необходимые для установления соединения между расположением сервера и расположение проекта, который находится под на диске Система управления версиями).  
  
 Системы управления версиями, VSPackage реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, который в свою очередь позволяет проектам регистрироваться для системы управления версиями и получить их состояние глифов.  
  
 Полный список интерфейсов, которые необходимо учитывать VSPackage системы управления версиями, см. в разделе [связанные службы и интерфейсы](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).  
  
## <a name="see-also"></a>См. также  
 [Элементы проектирования](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [Связанные службы и интерфейсы](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)


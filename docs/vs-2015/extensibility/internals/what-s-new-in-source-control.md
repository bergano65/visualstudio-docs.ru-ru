---
title: Новые возможности системы управления версиями
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 31b55c57f47f25814eff24f13bcf91408468d0f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200956"
---
# <a name="what39s-new-in-source-control-in-visual-studio-2015"></a>Новые&#39;в системе управления версиями в Visual Studio 2015

[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В можно [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] предоставить глубоко интегрированное решение системы управления версиями путем реализации пакета VSPackage системы управления версиями. В этом разделе описываются функции пакетов VSPackage системы управления версиями и приводятся общие сведения о шагах реализации.  
  
## <a name="the-source-control-vspackage"></a>Пакет VSPackage системы управления версиями  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] поддерживает два типа решений системы управления версиями. Во всех версиях служб [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] вы по-прежнему можете интегрировать подключаемый модуль на основе API для подключаемого модуля системы управления версиями. Также можно создать пакет VSPackage для системы управления версиями, обеспечивающий глубокую интеграцию, [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] подходящий для решений системы управления версиями, требующих высокого уровня сложности и автономности.  
  
 Пакет VSPackage может добавлять практически любые функции в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Пакет VSPackage системы управления версиями предоставляет полную функцию управления исходным кодом для [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , от пользовательского интерфейса, представленного пользователю, к серверной части связи с системой управления версиями.  
  
 Для реализации пакета VSPackage системы управления версиями требуется стратегия "все или ничего". Создатель пакета управления исходным кодом должен вкладывать значительный объем усилий в реализацию ряда интерфейсов системы управления версиями и новых элементов пользовательского интерфейса (диалоговых окон, меню и панелей инструментов) для реализации всей функциональности системы управления версиями, а также интерфейсов, необходимых для успешной интеграции пакета [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 Следующие шаги позволяют получить общие сведения о том, что необходимо для реализации пакета управления версиями. Дополнительные сведения см. [в разделе Создание пакета VSPackage системы управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
1. Создайте пакет VSPackage, профферс закрытую службу управления версиями.  
  
2. Реализуйте интерфейсы в службах, связанных с системой управления версиями, которые предложенной [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (например, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> интерфейс).  
  
3. Зарегистрируйте пакет VSPackage для системы управления версиями.  
  
4. Реализуйте весь пользовательский интерфейс системы управления версиями, включая пункты меню, диалоговые окна, панели инструментов и контекстные меню.  
  
5. Все события, связанные с системой управления версиями, передаются в систему управления версиями Всаккаже, когда она активна и должна обрабатываться пакетом VSPackage.  
  
6. Пакет VSPackage системы управления версиями должен прослушивать такие события, как реализация <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> интерфейса, а также отслеживание событий документа проекта (TPD) (в соответствии с реализацией <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> интерфейса) и выполнение необходимых действий.  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Средств](../../extensibility/internals/source-control-integration-overview.md)   
 [Создание пакета VSPackage системы управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md)

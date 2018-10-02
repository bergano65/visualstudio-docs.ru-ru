---
title: Обновление пользовательских проектов | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- upgrading project systems
- projects [Visual Studio SDK], upgrading
- project system upgrades [Visual Studio]
ms.assetid: 262ada44-7689-44d8-bacb-9c6d33834d4e
caps.latest.revision: 11
manager: douge
ms.openlocfilehash: 5c3fd31cfc7cfbf3f7dd687d38483f5bb62703ca
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47564228"
---
# <a name="upgrading-custom-projects"></a>Обновление пользовательских проектов
Если вы изменяете данные, сохраненные в файле проекта, при переводе продукта с одной версии Visual Studio на другую, то вам необходимо обеспечить обновление файла проекта со старой версии до новой. Для поддержки обновления, в котором позволяет участвовать в **мастера преобразования Visual Studio**, реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> интерфейс. Этот интерфейс содержит единственный доступный метод для обновления копии. Обновление проекта происходит в процессе открытия решения. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Интерфейс реализуется фабрикой проектов или по крайней мере должен доступная из фабрики проектов.  
  
 Старый механизм, который использует <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> интерфейс по-прежнему поддерживается, но по сути обновляет систему проекта в процессе открытия проекта. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Интерфейс называется таким образом [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] среды, даже если <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> вызывается или реализуется интерфейс. Такой подход позволяет использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> копирование реализовать только для частей обновления проекта и остальную часть работы, которые необходимо выполнить на месте (возможно, в новом расположении) <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> интерфейс.  
  
 Для реализации примера <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, см. в разделе [примеры VSSDK](../misc/vssdk-samples.md).  
  
 При обновлении проектов возникают описанные ниже ситуации.  
  
-   Если файл имеет более новый формат, который не поддерживается проектом, то должна возникать соответствующая ошибка. При этом предполагается, что в старой версии продукта, например в версии Visual Studio .NET 2003, есть код для проверки версии.  
  
-   Если <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> указан флаг <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> метод, обновление будет производиться обновление на месте перед открытием проекта.  
  
-   Если <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> указан флаг <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> метод, обновление реализуется как обновления копии.  
  
-   Если <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> указан флаг <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> вызвать, а затем пользователь получил запрос средой для обновления файла проекта как обновление на месте, после открытия проекта. Например, среда предлагает пользователю выполнить обновление, когда он открывает старую версию решения.  
  
-   Если <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> не указан флаг <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> вызвать, а затем должен предлагать пользователю выполнить обновление файла проекта.  
  
     Ниже приведен пример сообщения запроса на обновление.  
  
     "Проект "%1" был создан в старой версии Visual Studio. Если вы откроете его в этой версии Visual Studio, то после этого, возможно, не сможете открыть его в старых версиях Visual Studio. Продолжить и открыть проект?"  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>Реализация интерфейса IVsProjectUpgradeViaFactory  
  
1.  Реализуйте методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> интерфейс, в частности <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> метод в реализации фабрики проектов, или Обеспечьте можно вызывать из реализации фабрики проектов.  
  
2.  Если вы хотите выполнить обновление на месте в процессе открытия решения, укажите флаг <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> как `VSPUVF_FLAGS` параметр в вашей <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> реализации.  
  
3.  Если вы хотите выполнить обновление на месте в процессе открытия решения, укажите флаг <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> как `VSPUVF_FLAGS` параметр в вашей <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> реализации.  
  
4.  Для шагов 2 и 3, с помощью действия по обновлению фактический файл <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>, можно реализовать, как описано в разделе «Реализация `IVsProjectUpgade`"разделе ниже, или вы можете делегировать обновления файла <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
5.  Используйте методы класса <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> после обновления связанных сообщений для пользователя, с помощью мастера миграции Visual Studio.  
  
6.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> интерфейс используется для реализации любого типа обновления файлов, что должно происходить как часть обновления проекта. Этот интерфейс не вызывается из <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, а предоставляется как механизм для обновления файлов, которые являются частью системы проекта, но основной системе проекта не может быть напрямую ставить об. Например, такая ситуация может возникнуть, если связанными с компилятором файлами и свойствами с одной стороны и остальной системой проекта с другой стороны занимаются разные команды разработчиков.  
  
## <a name="ivsprojectupgrade-implementation"></a>Реализация интерфейса IVsProjectUpgrade  
 Если реализует систему проектов <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> , он не может участвовать в **мастера преобразования Visual Studio**. Тем не менее даже если вы реализуете <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> интерфейс, вы можете по-прежнему делегировать для обновления файлов <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> реализации.  
  
#### <a name="to-implement-ivsprojectupgrade"></a>Реализация интерфейса IVsProjectUpgrade  
  
1.  Когда пользователь пытается открыть проект, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> метод вызывается средой после открытия проекта и перед другими пользователями действия могут выполняться над проектом. Если пользователь уже получил запрос на обновление решения, а затем <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> флаг передается в `grfUpgradeFlags` параметра. Если пользователь открывает проект напрямую, таких как с помощью **добавить существующий проект** команды, то <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> флаг не передается и проект должен запрашивать пользователя для обновления.  
  
2.  В ответ на <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> вызова, проект должен определить, является ли файл проекта обновляется. Если проект не нужно обновлять до новой версии типа проекта, то он может просто возвращать <xref:Microsoft.VisualStudio.VSConstants.S_OK> флаг.  
  
3.  Если проект должен выполнить обновление до новой версии типа проекта, то он должен определить, можно ли изменить файл проекта, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> и передав значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> для `rgfQueryEdit` параметра. Затем проекту необходимо выполнить указанные ниже действия.  
  
    -   Если `VSQueryEditResult` значением, возвращенным `pfEditCanceled` параметр <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>, то обновление может продолжаться, так как файл проекта возможна.  
  
    -   Если `VSQueryEditResult` значением, возвращенным `pfEditCanceled` параметр <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> и `VSQueryEditResult` имеет значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> битом, затем <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> должен вернуть ошибку, так как пользователи должны решить проблему с разрешениями самостоятельно. После этого проект должен выполнить следующее действие:  
  
         Сообщить об ошибке для пользователя путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>. и возвращают <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> код ошибки, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
    -   Если `VSQueryEditResult` значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> и `VSQueryEditResultFlags` имеет значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> бит, а затем следует извлечь файл проекта, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>,...).  
  
4.  Если <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> вызов для файла проекта приводит файл для извлечения и последней версии, чтобы извлечь, а затем проект будет выгружен или перезагружен. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Метод вызывается снова, после создания другого экземпляра проекта. При втором вызове файл проекта можно записать на диск. Рекомендуется, чтобы проект сохранил копию файла проекта в старом формате с расширением OLD, внес необходимые в связи с обновлением изменения, а затем сохранил файл проекта в новом формате. Опять же, при сбое любой части процесса обновления, метод должен сообщить об этом, возвращая <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>. Это приводит к выгрузке проекта в обозревателе решений.  
  
     Очень важно полностью понимать процесс, в среде для ситуации, в которой происходит вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> метод (с указанием значения ReportOnly) возвращает <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> и <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> флаги.  
  
5.  Пользователь пытается открыть файл проекта.  
  
6.  Среда вызывает метод вашей <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> реализации.  
  
7.  Если <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> возвращает `true`, то среда вызывает метод вашей <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> реализации.  
  
8.  Среда вызывает метод вашей <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> реализации для открытия файла и инициализации объекта проекта, например, Project1.  
  
9. Среда вызывает вашу реализацию метода `IVsProjectUpgrade::UpgradeProject` , чтобы определить, необходимо ли обновить файл проекта.  
  
10. Вы вызываете <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> и передайте значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> для `rgfQueryEdit` параметра.  
  
11. Среда возвращает <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> для `VSQueryEditResult` и <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> бит задан в `VSQueryEditResultFlags`.  
  
12. Ваш <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> реализация вызывает `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>).  
  
 Этот вызов может привести к получению новой копии файла проекта для изменения и извлечению последней версии, а также к необходимости перезагрузить файл проекта. На этом этапе происходит одно из двух указанных ниже действий.  
  
-   Если вы обрабатываете перезагрузку проекта, среда вызывает ваш <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> реализации (VSITEMID_ROOT). Получив этот вызов, перезагрузите первый экземпляр проекта (Project1) и продолжайте обновление файла проекта. Среда определяет, обрабатывать перезагрузку проекта, если возвращается `true` для <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>).  
  
-   Если вы не обеспечиваете перезагрузку проекта, а затем вернетесь `false` для <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>). В этом случае перед <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>([QEF_ForceEdit_NoPrompting](assetId:///T:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags?qualifyHint=False&autoUpgrade=True), [QEF_DisallowInMemoryEdits](assetId:///T:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags?qualifyHint=False&autoUpgrade=True),) возвращает, среда создает еще один экземпляр проекта, например Project2, как выглядит следующим образом:  
  
    1.  Среда вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> на первого объекта проекта, Project1 таким образом размещение этого объекта в неактивное состояние.  
  
    2.  Среда вызывает вашу реализацию метода `IVsProjectFactory::CreateProject` , чтобы создать второй экземпляр проекта (Project2).  
  
    3.  Среда вызывает вашу реализацию метода `IPersistFileFormat::Load` для открытия файла и инициализации второго объекта проекта (Project2).  
  
    4.  Среда вызывает метод `IVsProjectUpgrade::UpgradeProject` второй раз, чтобы определить, следует ли обновить объект проекта. Однако этот вызов выполняется для второго экземпляра проекта (Project2). Это проект, который открыт в решении.  
  
        > [!NOTE]
        >  В экземпляре, в качестве первого проекта Project1 помещается в неактивное состояние, а затем должен возвращать <xref:Microsoft.VisualStudio.VSConstants.S_OK> из первого вызова вашего <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> реализации. См. в разделе [базовый проект](http://msdn.microsoft.com/en-us/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) реализацию `IVsProjectUpgrade::UpgradeProject`.  
  
    5.  Вы вызываете <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> и передайте значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> для `rgfQueryEdit` параметра.  
  
    6.  Среда возвращает <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> и обновление может продолжаться, так как файл проекта возможна.  
  
 Если вам не удается обновить, возвращают <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> из `IVsProjectUpgrade::UpgradeProject`. Если обновление не требуется или вы решили не производить его, вызов `IVsProjectUpgrade::UpgradeProject` следует рассматривать как холостой. Если возвращается <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>, узел-заполнитель добавляется в решение для проекта.  
  
## <a name="see-also"></a>См. также  
 [Мастер преобразования Visual Studio](http://msdn.microsoft.com/en-us/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Обновление элементов проекта](../misc/upgrading-project-items.md)   
 [Проекты](../extensibility/internals/projects.md)
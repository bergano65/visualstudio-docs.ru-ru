---
title: Обновление проектов | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cb64d71a50cb59a3c981dd87695bbb685f793761
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="upgrading-projects"></a>Обновление проектов
Изменения в модель проекта из одной версии [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] к следующему может потребоваться обновление проектов и решений, чтобы их можно запускать на более новой версии. [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Предоставляет интерфейсы, которые могут использоваться для реализации поддержки обновления в собственных проектах.  
  
## <a name="upgrade-strategies"></a>Стратегии обновления  
 Чтобы обеспечить поддержку обновления, реализации системы проекта необходимо указать и реализации стратегии обновления. При определении стратегии, можно выбрать для поддержки резервного копирования параллельные (SxS) и резервного копирования.  
  
-   Резервное копирование SxS означает, что проект копирует только те файлы, которым требуется обновление на месте, добавление подходящий файл суффикс имен, например, «расширения» OLD.  
  
-   Резервного копирования означает, что проект копирует все элементы проекта пользовательских местоположение для резервного копирования. Затем обновляются соответствующие файлы в исходное расположение проекта.  
  
## <a name="how-upgrade-works"></a>Как обновить Works  
 Если решения, созданного в более ранней версии [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] открыть в более новой версии проверок интегрированной среды разработки, файл решения для определения, если ее необходимо обновить. Если обновление является обязательным, **мастер обновления** автоматически запускается провести пользователя через процесс обновления.  
  
 При решении требуется обновление, он запрашивает каждой фабрики проектов для его стратегии обновления. Стратегия определяет, поддерживает ли фабрики проектов резервного копирования или резервного копирования SxS. Информация отправляется в **мастер обновления**, который собирает сведения, необходимые для резервного копирования и представлены параметры, применимые для пользователя.  
  
### <a name="multi-project-solutions"></a>Многопроектные решения  
 Если решение содержит несколько проектов и стратегии обновления отличаются, например, если проект C++, который поддерживает только SxS резервного копирования и веб-проекта, поддерживают только резервного копирования, в проекте фабрик должны согласовать стратегии обновления.  
  
 Решение запрашивает каждой фабрики проектов для <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. Затем он вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> для просмотра, если файлы глобальных проектов необходимо обновление, так и для определения поддерживаемых стратегии обновления. **Мастер обновления** затем вызывается.  
  
 После завершения мастера пользователем <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> вызывается для каждой фабрики проектов для выполнения фактического обновления. Чтобы упростить резервное копирование, предоставляют методы интерфейса IVsProjectUpgradeViaFactory <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> службу для записи сведений о процессе обновления. Эта служба не может быть кэширован.  
  
 После обновления все значимые файлы глобальных каждой фабрики проектов можно создать проект. Реализация проекта должна поддерживать <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Затем вызывается метод для обновления всех элементов соответствующего проекта.  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> Метод не предоставляет службу SVsUpgradeLogger. Эту службу можно получить путем вызова <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>.  
  
## <a name="best-practices"></a>Рекомендации  
 Используйте <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> службы для проверки можно изменить файл, прежде чем изменять его и сохранить его перед сохранением. Это поможет резервного копирования и обновления реализаций обрабатывать файлы проекта в системе управления версиями, файлы с недостаточно разрешений и т. д.  
  
 Используйте <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> службы на всех этапах резервного копирования и обновления для предоставления информации о успешность процесса обновления.  
  
 Дополнительные сведения о резервном копировании и обновление проектов см. комментарии для интерфейса IVsProjectUpgrade в vsshell2.idl.  
  
## <a name="upgrading-custom-projects"></a> Обновление пользовательских проектов
Если вы изменяете данные, сохраненные в файле проекта, при переводе продукта с одной версии Visual Studio на другую, то вам необходимо обеспечить обновление файла проекта со старой версии до новой. Для обеспечения обновления позволяет участвовать в **мастера преобразования Visual Studio**, реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> интерфейса. Этот интерфейс содержит единственный доступный метод для обновления копии. Обновление проекта происходит в процессе открытия решения. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Интерфейс реализуется фабрикой проектов или по крайней мере должен доступен из фабрики проектов.  
  
 Старый механизм, который использует <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> интерфейс по-прежнему поддерживается, но по сути обновляет систему проектов в рамках открытого проекта. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Интерфейс называется таким образом [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] среды, даже если <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> вызывается или реализуется интерфейс. Такой подход позволяет использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> для реализации копирования и обновления только для частей проекта и остальную работу выполнять на месте (возможно, в новое место) <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> интерфейс.  
  
 Образец реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, в разделе [примеры VSSDK](http://aka.ms/vs2015sdksamples).  
  
 При обновлении проектов возникают описанные ниже ситуации.  
  
-   Если файл имеет более новый формат, который не поддерживается проектом, то должна возникать соответствующая ошибка. Предполагается, что более старые версии продукта включает код для проверки версии.  
  
-   Если <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> установлен флаг в <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> метод, обновление будет производиться обновление на месте перед открытием проекта.  
  
-   Если <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> установлен флаг в <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> метод обновления реализуется в виде обновления копии.  
  
-   Если <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> установлен флаг в <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> вызвать, а затем для обновления файла проекта как для обновления на месте после открытия проекта пользователь приглашению средой. Например, среда предлагает пользователю выполнить обновление, когда он открывает старую версию решения.  
  
-   Если <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> флаг не указан в <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> вызове, необходимо предложить пользователю обновления файла проекта.  
  
     Ниже приведен пример сообщения запроса на обновление.  
  
     "Проект "%1" был создан в старой версии Visual Studio. Если вы откроете его в этой версии Visual Studio, то после этого, возможно, не сможете открыть его в старых версиях Visual Studio. Продолжить и открыть проект?"  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>Реализация интерфейса IVsProjectUpgradeViaFactory  
  
1.  Реализуйте методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> интерфейс, в частности <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> метод в реализации фабрики проектов или Обеспечьте может быть вызван из реализации фабрики проектов.  
  
2.  Если вы хотите выполнить обновление на месте в процессе открытия решения, укажите флаг <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> как `VSPUVF_FLAGS` параметр в вашей <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> реализации.  
  
3.  Если вы хотите выполнить обновление на месте в процессе открытия решения, укажите флаг <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> как `VSPUVF_FLAGS` параметр в вашей <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> реализации.  
  
4.  Для шагов 2 и 3, с помощью действия по обновлению сам файл <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>, можно реализовать, как описано в «реализация `IVsProjectUpgade`"ниже, в разделе, или вы можете делегировать обновления файла <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
5.  Используйте методы класса <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> после обновления, связанные с сообщений для пользователя, с помощью мастера миграции Visual Studio.  
  
6.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> интерфейс используется для реализации любого типа обновления файлов, которое должно происходить в рамках обновления проекта. Этот интерфейс не вызывается из <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, а предоставляется как механизм для обновления файлов, которые входят в систему проекта, но в основной системе проекта не может быть непосредственно учитывать. Например, такая ситуация может возникнуть, если связанными с компилятором файлами и свойствами с одной стороны и остальной системой проекта с другой стороны занимаются разные команды разработчиков.  
  
### <a name="ivsprojectupgrade-implementation"></a>Реализация интерфейса IVsProjectUpgrade  
 Если системе проекта реализован <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> , он не может участвовать в **мастера преобразования Visual Studio**. Тем не менее даже если вы реализуете <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> интерфейса, можно по-прежнему делегировать для обновления файлов <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> реализации.  
  
#### <a name="to-implement-ivsprojectupgrade"></a>Реализация интерфейса IVsProjectUpgrade  
  
1.  Когда пользователь пытается открыть проект, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> метод вызывается средой после открытия проекта и перед любой другой пользователь действия выполняются в проекте. Если пользователь уже получил запрос на обновление решения, а затем <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> флаг передается в `grfUpgradeFlags` параметра. Если пользователь открывает проект напрямую, например с помощью **добавить существующий проект** команду, а затем <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> флаг не передается и проект должен запрашивать пользователя для обновления.  
  
2.  В ответ на <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> вызова, проект должен определить, является ли обновляться файл проекта. Если проект не нужно обновлять до новой версии типа проекта, то он может просто возвращать <xref:Microsoft.VisualStudio.VSConstants.S_OK> флаг.  
  
3.  Если необходимо добавить в проект для обновления до новой версии типа проекта, то он должен определить, возможно ли изменение файла проекта путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> метод и передав значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> для `rgfQueryEdit` параметра. Затем проекту необходимо выполнить указанные ниже действия.  
  
    -   Если `VSQueryEditResult` значение, возвращаемое в `pfEditCanceled` параметр <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>, то обновление может продолжаться, так как файл проекта можно записать.  
  
    -   Если `VSQueryEditResult` значение, возвращаемое в `pfEditCanceled` параметр <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> и `VSQueryEditResult` имеет значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> бит, затем <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> должен вернуть ошибку, так как пользователи должны решить проблему с разрешениями самостоятельно. После этого проект должен выполнить следующее действие:  
  
         Отчет об ошибке пользователю путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> и возвращают <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> код ошибки, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
    -   Если `VSQueryEditResult` значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> и `VSQueryEditResultFlags` имеет значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> бит, то файл проекта должен быть извлечен, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>,...).  
  
4.  Если <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> вызов для файла проекта приводит файл был извлечен, а также последнюю версию, чтобы получить, то проект выгружается и перезагружена. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Вызывается снова после создания другой экземпляр проекта. При втором вызове файл проекта можно записать на диск. Рекомендуется, чтобы проект сохранил копию файла проекта в старом формате с расширением OLD, внес необходимые в связи с обновлением изменения, а затем сохранил файл проекта в новом формате. Еще раз, при сбое любой части процесс обновления, метод должен сообщить об этом, возвращая <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>. Это приводит к выгрузке проекта в обозревателе решений.  
  
     Очень важно полностью понимать процесс, который происходит в среде для случая, в котором вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> метод (с указанием значения ReportOnly) возвращает <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> и <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> флаги.  
  
5.  Пользователь пытается открыть файл проекта.  
  
6.  Среда вызывает метод вашей <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> реализации.  
  
7.  Если <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> возвращает `true`, то среда вызывает метод вашей <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> реализации.  
  
8.  Среда вызывает метод вашей <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> реализации для открытия файла и инициализации объекта проекта, например, Project1.  
  
9. Среда вызывает вашу реализацию метода `IVsProjectUpgrade::UpgradeProject` , чтобы определить, необходимо ли обновить файл проекта.  
  
10. Можно вызвать <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> и передайте значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> для `rgfQueryEdit` параметра.  
  
11. Среда возвращает <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> для `VSQueryEditResult` и <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> бит задан в `VSQueryEditResultFlags`.  
  
12. Ваш <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> реализация вызывает `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>).  
  
 Этот вызов может привести к получению новой копии файла проекта для изменения и извлечению последней версии, а также к необходимости перезагрузить файл проекта. На этом этапе происходит одно из двух указанных ниже действий.  
  
-   Если вы самостоятельно обеспечиваете перезагрузку проекта, среда вызывает вашей <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> реализацию (VSITEMID_ROOT). Получив этот вызов, перезагрузите первый экземпляр проекта (Project1) и продолжайте обновление файла проекта. Среда определяет, обрабатывать самостоятельно обеспечиваете перезагрузку проекта, если возвращается `true` для <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>).  
  
-   Если не следует обрабатывать самостоятельно обеспечиваете перезагрузку проекта, то возвращается `false` для <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>). В этом случае перед <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>(QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits) возвращает среда создает другой новый экземпляр проекта, например Project2 следующим образом:  
  
    1.  Среда вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> для первого объекта проекта, Project1, таким образом размещение этого объекта в неактивное состояние.  
  
    2.  Среда вызывает вашу реализацию метода `IVsProjectFactory::CreateProject` , чтобы создать второй экземпляр проекта (Project2).  
  
    3.  Среда вызывает вашу реализацию метода `IPersistFileFormat::Load` для открытия файла и инициализации второго объекта проекта (Project2).  
  
    4.  Среда вызывает метод `IVsProjectUpgrade::UpgradeProject` второй раз, чтобы определить, следует ли обновить объект проекта. Однако этот вызов выполняется для второго экземпляра проекта (Project2). Это проект, который открыт в решении.  
  
        > [!NOTE]
        >  В экземпляре, ваш первый проект Project1 помещается в неактивном состоянии, то необходимо вернуть <xref:Microsoft.VisualStudio.VSConstants.S_OK> из первого вызова вашей <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> реализации.  
  
    5.  Можно вызвать <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> и передайте значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> для `rgfQueryEdit` параметра.  
  
    6.  Среда возвращает <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> и обновление может продолжаться, так как файл проекта можно записать.  
  
 Если не удалось обновить, возвращают <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> из `IVsProjectUpgrade::UpgradeProject`. Если обновление не требуется или вы решили не производить его, вызов `IVsProjectUpgrade::UpgradeProject` следует рассматривать как холостой. Если возвращается <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>, решение для проекта добавляется узел-заполнитель.  
  
## <a name="upgrading-project-items"></a>Обновление элементов проекта
  
При добавлении или управлять элементами внутри системы проектов, которые не реализуют, может потребоваться участие в процессе обновления проекта. Crystal Reports является примером элемента, который может быть добавлен к системе проектов.  
  
 Как правило разработчики элемента проекта требуется использовать уже полностью созданный экземпляр и обновленный проект, так как им нужно знать, какие ссылки на проект и какие другие свойства проекта существуют для принятия решения об обновлении.  
  
### <a name="to-get-the-project-upgrade-notification"></a>Чтобы получать уведомления об обновлении проекта  
  
1.  Задать <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> флаг (определенная в vsshell80.idl) в такой реализации элемента проекта. В результате элемент проекта VSPackage, чтобы автоматически загрузить при [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] оболочки определяет, что система проектов в процессе обновления.  
  
2.  Уведомить <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> через интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> метод.  
  
3.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> Интерфейс возникает после завершения обновления реализации системы проекта и создан новый обновленный проект. В зависимости от сценария <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> интерфейс срабатывает после <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>, или <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> методы.  
  
### <a name="to-upgrade-the-project-item-files"></a>Чтобы обновить файлы элементов проекта  
  
1.  Необходимо тщательно управлять процесс резервного копирования файла в реализации элемента проекта. Это относится, в частности, side-by-side резервную копию, где `fUpgradeFlag` параметр <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> задан метод <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>, где находятся файлы, которые была сделана резервная копия вместе файлов стороны, которые обозначены как «расширения OLD». Файлы резервных копий, более ранней, чем системного времени, если проект был обновлен, назначается как устаревшая. Кроме того они могут быть перезаписаны, если не предпринять определенные действия, чтобы избежать этого.  
  
2.  Во время элемент проекта получает уведомление обновления проекта, **мастера преобразования Visual Studio** по-прежнему отображается. Таким образом, следует использовать методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> интерфейс для предоставления пользовательского интерфейса мастера обновления сообщения.  
  
## <a name="see-also"></a>См. также  
 [Проекты](../../extensibility/internals/projects.md)   

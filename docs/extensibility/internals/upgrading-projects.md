---
title: Обновление проектов | Документация Майкрософт
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
ms.openlocfilehash: ea5c29819d0035e45f97122fd108ea1f51d60806
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057538"
---
# <a name="upgrading-projects"></a>Обновление проектов

Изменения в модель проекта из одной версии Visual Studio к следующему может потребоваться обновление проекты и решения, чтобы они могут работать на более новой версии. [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Предоставляет интерфейсы, которые могут использоваться для реализации поддержки обновления в своих собственных проектах.

## <a name="upgrade-strategies"></a>Стратегии обновления

Для поддержки обновления, реализации системы проекта необходимо определить и реализовать стратегию обновления. В определении стратегии, вы можете для поддержки резервного копирования side-by-side (SxS) и резервного копирования.

-   Резервное копирование SxS означает, что проект копирует только те файлы, которые требуется обновление на месте, добавив подходящий файл суффикса имени, например, «расширения» OLD.

-   Резервная копия для копирования означает, что проект копирует все элементы проекта папку резервного копирования, предоставляемый пользователем. Затем обновляются соответствующие файлы в исходное расположение проекта.

## <a name="how-upgrade-works"></a>О принципах работы обновления

При открытии решения, созданного в более ранней версии Visual Studio в более новой версии интегрированной среды разработки проверяет файл решения, чтобы определить, если он должен быть обновлен. Если обновление является обязательным, **мастер обновления** запускается автоматически, чтобы ознакомить пользователя через процесс обновления.

При решении необходимо обновить, он запрашивает Каждая фабрика проекта для его обновления стратегии. Стратегия определяет, поддерживает ли фабрика проектов резервного копирования или резервного копирования SxS. Информация отправляется **мастер обновления**, который собирает сведения, необходимые для резервного копирования и пользователю предоставляются соответствующие флажки.

### <a name="multi-project-solutions"></a>Многопроектные решения

Если решение содержит несколько проектов и стратегии обновления отличаются, например, при создании проекта C++, который поддерживает только резервное копирование SxS и проект веб-приложения поддерживают только резервного копирования, фабрик проектов должны согласовывать стратегии обновления.

Решение запрашивает Каждая фабрика проекта для <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. Затем он вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> см. в разделе, если файлы глобальных проектов требуется обновление и определение поддерживаемых стратегии обновления. **Мастер обновления** затем вызывается.

Как только пользователь завершит мастера <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> вызывается для каждой фабрики проекта для выполнения фактического обновления. Для упрощения резервного копирования, предоставляют методы интерфейса IVsProjectUpgradeViaFactory <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> службу для записи сведений о процессе обновления. Эта служба не может кэшироваться.

После обновления все соответствующие файлы глобального, каждая фабрика проекта можно создать экземпляр проекта. Реализация проекта должна поддерживать <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Затем вызывается метод для обновления всех элементов соответствующего проекта.

> [!NOTE]
> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> Метод не предоставляет службу SVsUpgradeLogger. Эту службу можно получить путем вызова <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>.

## <a name="best-practices"></a>Рекомендации

Используйте <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> службы, чтобы проверить можно изменить файл, прежде чем изменять его, а затем сохранить их перед сохранением. Это поможет резервного копирования и обновления реализаций обрабатывать файлы проекта в системе управления версиями, файлы с недостаточно разрешений и т. д.

Используйте <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> службы во время всех этапов резервное копирование и обновление для предоставления сведений об успешности выполнения процесса обновления.

Дополнительные сведения о резервном копировании и обновление проектов см. в разделе комментариев для интерфейса IVsProjectUpgrade в vsshell2.idl.

## <a name="upgrading-custom-projects"></a> Обновление пользовательских проектов

Если вы изменяете данные, сохраненные в файле проекта, при переводе продукта с одной версии Visual Studio на другую, то вам необходимо обеспечить обновление файла проекта со старой версии до новой. Для поддержки обновления, в котором позволяет участвовать в **мастера преобразования Visual Studio**, реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> интерфейс. Этот интерфейс содержит единственный доступный метод для обновления копии. Обновление проекта происходит в процессе открытия решения. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Интерфейс реализуется фабрикой проектов или по крайней мере должен доступная из фабрики проектов.

Старый механизм, который использует <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> интерфейс по-прежнему поддерживается, но по сути обновляет систему проекта в процессе открытия проекта. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Интерфейса таким образом вызывается среды Visual Studio, даже если <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> вызывается или реализуется интерфейс. Такой подход позволяет использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> копирование реализовать только для частей обновления проекта и остальную часть работы, которые необходимо выполнить на месте (возможно, в новом расположении) <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> интерфейс.

Для реализации примера <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, см. в разделе [примеры VSSDK](http://aka.ms/vs2015sdksamples).

При обновлении проектов возникают описанные ниже ситуации.

-   Если файл имеет более новый формат, который не поддерживается проектом, то должна возникать соответствующая ошибка. При этом предполагается, что более раннюю версию продукта включает код для проверки версии.

-   Если <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> указан флаг <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> метод, обновление будет производиться обновление на месте перед открытием проекта.

-   Если <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> указан флаг <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> метод, обновление реализуется как обновления копии.

-   Если <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> указан флаг <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> вызвать, а затем пользователь получил запрос средой для обновления файла проекта как обновление на месте, после открытия проекта. Например, среда предлагает пользователю выполнить обновление, когда он открывает старую версию решения.

-   Если <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> не указан флаг <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> вызвать, а затем должен предлагать пользователю выполнить обновление файла проекта.

     Ниже приведен пример сообщения запроса на обновление.

     "Проект "%1" был создан в старой версии Visual Studio. Если вы откроете его в этой версии Visual Studio, то после этого, возможно, не сможете открыть его в старых версиях Visual Studio. Продолжить и открыть проект?"

### <a name="to-implement-ivsprojectupgradeviafactory"></a>Реализация интерфейса IVsProjectUpgradeViaFactory

1.  Реализуйте методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> интерфейс, в частности <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> метод в реализации фабрики проектов, или Обеспечьте можно вызывать из реализации фабрики проектов.

2.  Если вы хотите выполнить обновление на месте в процессе открытия решения, укажите флаг <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> как `VSPUVF_FLAGS` параметр в вашей <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> реализации.

3.  Если вы хотите выполнить обновление на месте в процессе открытия решения, укажите флаг <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> как `VSPUVF_FLAGS` параметр в вашей <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> реализации.

4.  Для шагов 2 и 3, с помощью действия по обновлению фактический файл <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>, можно реализовать, как описано в разделе «Реализация `IVsProjectUpgade`"разделе ниже, или вы можете делегировать обновления файла <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

5.  Используйте методы класса <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> после обновления связанных сообщений для пользователя, с помощью мастера миграции Visual Studio.

6.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> интерфейс используется для реализации любого типа обновления файлов, что должно происходить как часть обновления проекта. Этот интерфейс не вызывается из <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, а предоставляется как механизм для обновления файлов, которые являются частью системы проекта, но основной системе проекта не может быть напрямую ставить об. Например, такая ситуация может возникнуть, если связанными с компилятором файлами и свойствами с одной стороны и остальной системой проекта с другой стороны занимаются разные команды разработчиков.

### <a name="ivsprojectupgrade-implementation"></a>Реализация интерфейса IVsProjectUpgrade

Если реализует систему проектов <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> , он не может участвовать в **мастера преобразования Visual Studio**. Тем не менее даже если вы реализуете <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> интерфейс, вы можете по-прежнему делегировать для обновления файлов <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> реализации.

#### <a name="to-implement-ivsprojectupgrade"></a>Реализация интерфейса IVsProjectUpgrade

1.  Когда пользователь пытается открыть проект, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> метод вызывается средой после открытия проекта и перед другими пользователями действия могут выполняться над проектом. Если пользователь уже получил запрос на обновление решения, а затем <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> флаг передается в `grfUpgradeFlags` параметра. Если пользователь открывает проект напрямую, таких как с помощью **добавить существующий проект** команды, то <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> флаг не передается и проект должен запрашивать пользователя для обновления.

2.  В ответ на <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> вызова, проект должен определить, является ли файл проекта обновляется. Если проект не нужно обновлять до новой версии типа проекта, то он может просто возвращать <xref:Microsoft.VisualStudio.VSConstants.S_OK> флаг.

3.  Если проект должен выполнить обновление до новой версии типа проекта, то он должен определить, можно ли изменить файл проекта, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> и передав значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> для `rgfQueryEdit` параметра. Затем проекту необходимо выполнить указанные ниже действия.

    -   Если `VSQueryEditResult` значением, возвращенным `pfEditCanceled` параметр <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>, то обновление может продолжаться, так как файл проекта возможна.

    -   Если `VSQueryEditResult` значением, возвращенным `pfEditCanceled` параметр <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> и `VSQueryEditResult` имеет значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc> битом, затем <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> должен вернуть ошибку, так как пользователи должны решить проблему с разрешениями самостоятельно. После этого проект должен выполнить следующее действие:

         Сообщить об ошибке для пользователя, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> и вернуть <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> код ошибки, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

    -   Если `VSQueryEditResult` значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> и `VSQueryEditResultFlags` имеет значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> бит, а затем следует извлечь файл проекта, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>,...).

4.  Если <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> вызов для файла проекта приводит файл для извлечения и последней версии, чтобы извлечь, а затем проект будет выгружен или перезагружен. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Метод вызывается снова, после создания другого экземпляра проекта. При втором вызове файл проекта можно записать на диск. Рекомендуется, чтобы проект сохранил копию файла проекта в старом формате с расширением OLD, внес необходимые в связи с обновлением изменения, а затем сохранил файл проекта в новом формате. Опять же, при сбое любой части процесса обновления, метод должен сообщить об этом, возвращая <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>. Это приводит к выгрузке проекта в обозревателе решений.

     Очень важно полностью понимать процесс, в среде для ситуации, в которой происходит вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> метод (с указанием значения ReportOnly) возвращает <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> и <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> флаги.

5.  Пользователь пытается открыть файл проекта.

6.  Среда вызывает метод вашей <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> реализации.

7.  Если <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> возвращает `true`, то среда вызывает метод вашей <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> реализации.

8.  Среда вызывает метод вашей <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> реализации для открытия файла и инициализации объекта проекта, например, Project1.

9. Среда вызывает вашу реализацию метода `IVsProjectUpgrade::UpgradeProject` , чтобы определить, необходимо ли обновить файл проекта.

10. Вы вызываете <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> и передайте значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> для `rgfQueryEdit` параметра.

11. Среда возвращает <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> для `VSQueryEditResult` и <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> бит задан в `VSQueryEditResultFlags`.

12. Ваш <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> реализация вызывает `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>).

Этот вызов может привести к получению новой копии файла проекта для изменения и извлечению последней версии, а также к необходимости перезагрузить файл проекта. На этом этапе происходит одно из двух указанных ниже действий.

-   Если вы обрабатываете перезагрузку проекта, среда вызывает ваш <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> реализации (VSITEMID_ROOT). Получив этот вызов, перезагрузите первый экземпляр проекта (Project1) и продолжайте обновление файла проекта. Среда определяет, обрабатывать перезагрузку проекта, если возвращается `true` для <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>).

-   Если вы не обеспечиваете перезагрузку проекта, а затем вернетесь `false` для <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>). В этом случае перед <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>(QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits) возвращает среде создает еще один новый экземпляр проекта, например Project2, следующим образом:

    1.  Среда вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> на первого объекта проекта, Project1 таким образом размещение этого объекта в неактивное состояние.

    2.  Среда вызывает вашу реализацию метода `IVsProjectFactory::CreateProject` , чтобы создать второй экземпляр проекта (Project2).

    3.  Среда вызывает вашу реализацию метода `IPersistFileFormat::Load` для открытия файла и инициализации второго объекта проекта (Project2).

    4.  Среда вызывает метод `IVsProjectUpgrade::UpgradeProject` второй раз, чтобы определить, следует ли обновить объект проекта. Однако этот вызов выполняется для второго экземпляра проекта (Project2). Это проект, который открыт в решении.

        > [!NOTE]
        > В экземпляре, в качестве первого проекта Project1 помещается в неактивное состояние, а затем должен возвращать <xref:Microsoft.VisualStudio.VSConstants.S_OK> из первого вызова вашего <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> реализации.

    5.  Вы вызываете <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> и передайте значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> для `rgfQueryEdit` параметра.

    6.  Среда возвращает <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK> и обновление может продолжаться, так как файл проекта возможна.

Если вам не удается обновить, возвращают <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> из `IVsProjectUpgrade::UpgradeProject`. Если обновление не требуется или вы решили не производить его, вызов `IVsProjectUpgrade::UpgradeProject` следует рассматривать как холостой. Если возвращается <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>, узел-заполнитель добавляется в решение для проекта.

## <a name="upgrading-project-items"></a>Обновление элементов проекта

При добавлении или управлять элементами внутри системы проектов, которые не реализуют, может потребоваться принять участие в процессе обновления проекта. Crystal Reports является примером элемента, который можно добавить в систему проектов.

Как правило реализации элемента проекта нужно использовать уже полностью созданным экземпляром и обновленного проекта, так как им нужно знать, какие ссылки на проект и какие другие свойства проекта есть для принятия решения об обновлении.

### <a name="to-get-the-project-upgrade-notification"></a>Чтобы получить уведомление об обновлении проекта

1.  Задайте <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> флаг (определенных в файле vsshell80.idl) в реализации элемента проекта. Это вызывает элемента проекта VSPackage для автоматической загрузки, если оболочка Visual Studio определяет, что система проектов находится в процессе обновления.

2.  Уведомить <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> интерфейс через <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> метод.

3.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> Интерфейс срабатывает после реализации системы проекта завершении обновления и создается новый обновленный проект. В зависимости от сценария <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> интерфейс срабатывает после <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>, или <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> методы.

### <a name="to-upgrade-the-project-item-files"></a>Чтобы обновить файлы элементов проекта

1.  Необходимо тщательно управлять процесс резервного копирования файла в реализации элемента проекта. Это относится, в частности, для резервного копирования side-by-side, где `fUpgradeFlag` параметр <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> задан метод <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP>, куда помещаются файлы, которые созданы резервные копии вдоль стороны файлы, которые обозначены как «расширения» OLD. Старше системное время, когда проект был обновлен файла резервной копии может быть назначен как устаревший. Кроме того они могут быть перезаписаны, если только вы выполнить определенные действия, чтобы избежать этого.

2.  Во время вашего элемента проекта получает уведомление о обновления проекта, **мастера преобразования Visual Studio** по-прежнему отображается. Таким образом, следует использовать методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> интерфейс для предоставления сообщений обновления пользовательского интерфейса мастера.

## <a name="see-also"></a>См. также

- [Проекты](../../extensibility/internals/projects.md)
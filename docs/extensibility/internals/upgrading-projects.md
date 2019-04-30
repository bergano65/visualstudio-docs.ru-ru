---
title: Обновление проектов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5aac06c9d06145f288a64deb210e3c8cb1bd2bd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62857732"
---
# <a name="upgrading-projects"></a>Обновление проектов

Изменения в модель проекта из одной версии Visual Studio к следующему может потребоваться обновление проекты и решения, чтобы они могут работать на более новой версии. [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Предоставляет интерфейсы, которые могут использоваться для реализации поддержки обновления в своих собственных проектах.

## <a name="upgrade-strategies"></a>Стратегии обновления

Для поддержки обновления, реализации системы проекта необходимо определить и реализовать стратегию обновления. В определении стратегии, вы можете для поддержки резервного копирования side-by-side (SxS) и резервного копирования.

- Резервное копирование SxS означает, что проект копирует только те файлы, которые требуется обновление на месте, добавив подходящий файл суффикса имени, например, «расширения» OLD.

- Резервная копия для копирования означает, что проект копирует все элементы проекта папку резервного копирования, предоставляемый пользователем. Затем обновляются соответствующие файлы в исходное расположение проекта.

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

Если вы изменяете данные, сохраненные в файле проекта, при переводе продукта с одной версии Visual Studio на другую, то вам необходимо обеспечить обновление файла проекта со старой версии до новой. Для поддержки обновления, в котором позволяет участвовать в **мастера преобразования Visual Studio**, реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> интерфейс. Этот интерфейс содержит единственный доступный метод для обновления копии. Обновление проекта происходит в процессе открытия решения. Интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> реализуется фабрикой проектов или по крайней мере должен получаться из нее.

Старый механизм, предполагающий использование интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, по-прежнему поддерживается, но по сути обновляет систему проекта в процессе открытия проекта. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Интерфейса таким образом вызывается среды Visual Studio, даже если <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> вызывается или реализуется интерфейс. Такой подход позволяет использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> для реализации обновления с копированием только для частей проекта, а остальную работу выполнять на месте (возможно, в новом расположении) с помощью интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

Для реализации примера <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, см. в разделе [примеры VSSDK](https://aka.ms/vs2015sdksamples).

При обновлении проектов возникают описанные ниже ситуации.

- Если файл имеет более новый формат, который не поддерживается проектом, то должна возникать соответствующая ошибка. При этом предполагается, что более раннюю версию продукта включает код для проверки версии.

- Если в методе <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> указан флаг <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP>, будет производиться обновление на месте перед открытием проекта.

- Если в методе <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> указан флаг <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP>, производится обновление с копированием.

- Если в вызове <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> указан флаг <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE>, пользователь получил от среды запрос на обновление файла проекта на месте после открытия проекта. Например, среда предлагает пользователю выполнить обновление, когда он открывает старую версию решения.

- Если в вызове <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> не указан флаг <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE>, то вы должны обеспечить вывод запроса на обновление файла проекта.

     Ниже приведен пример сообщения запроса на обновление.

     "Проект "%1" был создан в старой версии Visual Studio. Если вы откроете его в этой версии Visual Studio, то после этого, возможно, не сможете открыть его в старых версиях Visual Studio. Продолжить и открыть проект?"

### <a name="to-implement-ivsprojectupgradeviafactory"></a>Реализация интерфейса IVsProjectUpgradeViaFactory

1. Реализуйте методы интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, в частности метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>, в реализации фабрики проектов или обеспечьте возможность вызова этих методов из реализации фабрики проектов.

2. Если в процессе открытия решения необходимо произвести обновление на месте, укажите флаг <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> в качестве параметра `VSPUVF_FLAGS` в реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>.

3. Если в процессе открытия решения необходимо произвести обновление на месте, укажите флаг <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> в качестве параметра `VSPUVF_FLAGS` в реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>.

4. Для шагов 2 и 3 непосредственные действия по обновлению файла с использованием интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> можно реализовать, как описано в приведенном ниже разделе "Реализация интерфейса `IVsProjectUpgade`". Процесс обновления файла можно также реализовать с помощью интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

5. Используйте методы интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> для вывода связанных с обновлением сообщений для пользователя с помощью мастера миграции Visual Studio.

6. Интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> используется для реализации любого типа обновления файлов, которое должно происходить в рамках обновления проекта. Этот интерфейс не вызывается из <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, а предоставляется как механизм для обновления файлов, которые входят в систему проекта, но сведения о которых могут отсутствовать в основной системе проекта. Например, такая ситуация может возникнуть, если связанными с компилятором файлами и свойствами с одной стороны и остальной системой проекта с другой стороны занимаются разные команды разработчиков.

### <a name="ivsprojectupgrade-implementation"></a>Реализация интерфейса IVsProjectUpgrade

Если реализует систему проектов <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> , он не может участвовать в **мастера преобразования Visual Studio**. Однако даже если вы реализуете интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, вы все же можете задействовать реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> для обновления файлов.

#### <a name="to-implement-ivsprojectupgrade"></a>Реализация интерфейса IVsProjectUpgrade

1. Когда пользователь пытается открыть проект, метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> вызывается средой сразу после открытия проекта. Любые действия пользователя с проектом могут совершаться только после выполнения этого метода. Если пользователь уже получил запрос на обновление решения, флаг <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> передается в параметре `grfUpgradeFlags`. Если пользователь открывает проект напрямую, таких как с помощью **добавить существующий проект** команды, то <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> флаг не передается и проект должен запрашивать пользователя для обновления.

2. В ответ на вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> проект должен определить, должен ли обновляться файл проекта. Если тип проекта не нужно обновлять до новой версии, то проект может просто вернуть флаг <xref:Microsoft.VisualStudio.VSConstants.S_OK>.

3. Если тип проекта нужно обновить до новой версии, следует определить, можно ли изменить файл проекта, вызвав метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> и передав значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> для параметра `rgfQueryEdit`. Затем проекту необходимо выполнить указанные ниже действия.

    - Если значение `VSQueryEditResult`, возвращаемое в параметре `pfEditCanceled`, равно <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>, обновление может продолжаться, так как запись в файл проекта возможна.

    - Если значение `VSQueryEditResult`, возвращаемое в параметре `pfEditCanceled`, равно <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> и в значении `VSQueryEditResult` задан бит <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc>, то метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> должен вернуть ошибку, так как пользователи должны решить проблему с разрешениями самостоятельно. После этого проект должен выполнить следующее действие:

         Сообщить об ошибке для пользователя, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> и вернуть <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> код ошибки, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

    - Если значение `VSQueryEditResult` равно <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> и в значении `VSQueryEditResultFlags` задан бит <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc>, то файл проекта следует получить для изменения, вызвав метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>...).

4. Если вызов метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> для файла проекта приводит к получению этого файла для изменения и извлечению последней версии, то проект выгружается и загружается повторно. После создания еще одного экземпляра проекта метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> вызывается повторно. При втором вызове файл проекта можно записать на диск. Рекомендуется, чтобы проект сохранил копию файла проекта в старом формате с расширением OLD, внес необходимые в связи с обновлением изменения, а затем сохранил файл проекта в новом формате. Если на каком-либо этапе процесса обновления происходит сбой, метод должен сообщить об этом, вернув код ошибки <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>. Это приводит к выгрузке проекта в обозревателе решений.

     Важно полностью понимать процесс, который происходит в среде в случае, если вызов метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (с указанием значения ReportOnly) возвращает флаги <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> и <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc>.

5. Пользователь пытается открыть файл проекта.

6. Среда вызывает вашу реализацию метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>.

7. Если метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> возвращает значение `true`, среда вызывает вашу реализацию метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>.

8. Среда вызывает вашу реализацию метода <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> для открытия файла и инициализации объекта проекта, например Project1.

9. Среда вызывает вашу реализацию метода `IVsProjectUpgrade::UpgradeProject` , чтобы определить, необходимо ли обновить файл проекта.

10. Вы вызываете метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> и передаете значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> для параметра `rgfQueryEdit`.

11. Среда возвращает значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> для `VSQueryEditResult`, а в `VSQueryEditResultFlags` устанавливается бит <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc>.

12. Ваша реализация интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> вызывает `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>).

Этот вызов может привести к получению новой копии файла проекта для изменения и извлечению последней версии, а также к необходимости перезагрузить файл проекта. На этом этапе происходит одно из двух указанных ниже действий.

- Если вы самостоятельно обеспечиваете перезагрузку проекта, то среда вызывает вашу реализацию метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (VSITEMID_ROOT). Получив этот вызов, перезагрузите первый экземпляр проекта (Project1) и продолжайте обновление файла проекта. Среда определяет, что вы самостоятельно обеспечиваете перезагрузку проекта, если для <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>) возвращается значение `true`.

- Если вы не обеспечиваете перезагрузку проекта самостоятельно, то для <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>) должно возвращаться значение `false`. В этом случае перед <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>(QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits) возвращает среде создает еще один новый экземпляр проекта, например Project2, следующим образом:

    1. Среда вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> для первого объекта проекта (Project1), переводя его таким образом в неактивное состояние.

    2. Среда вызывает вашу реализацию метода `IVsProjectFactory::CreateProject` , чтобы создать второй экземпляр проекта (Project2).

    3. Среда вызывает вашу реализацию метода `IPersistFileFormat::Load` для открытия файла и инициализации второго объекта проекта (Project2).

    4. Среда вызывает метод `IVsProjectUpgrade::UpgradeProject` второй раз, чтобы определить, следует ли обновить объект проекта. Однако этот вызов выполняется для второго экземпляра проекта (Project2). Это проект, который открыт в решении.

        > [!NOTE]
        > В случае если первый проект (Project1) переведен в неактивное состояние, в результате первого вызова реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> должно возвращаться значение <xref:Microsoft.VisualStudio.VSConstants.S_OK>.

    5. Вы вызываете метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> и передаете значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> для параметра `rgfQueryEdit`.

    6. Среда возвращает значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>, и обновление может продолжаться, так как запись в файл проекта возможна.

В случае сбоя обновления метод `IVsProjectUpgrade::UpgradeProject` должен возвращать значение <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>. Если обновление не требуется или вы решили не производить его, вызов `IVsProjectUpgrade::UpgradeProject` следует рассматривать как холостой. Если возвращается код ошибки <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>, в решение проекта добавляется узел-заполнитель.

## <a name="upgrading-project-items"></a>Обновление элементов проекта

При добавлении или управлять элементами внутри системы проектов, которые не реализуют, может потребоваться принять участие в процессе обновления проекта. Crystal Reports является примером элемента, который можно добавить в систему проектов.

Как правило реализации элемента проекта нужно использовать уже полностью созданным экземпляром и обновленного проекта, так как им нужно знать, какие ссылки на проект и какие другие свойства проекта есть для принятия решения об обновлении.

### <a name="to-get-the-project-upgrade-notification"></a>Чтобы получить уведомление об обновлении проекта

1. Задайте <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> флаг (определенных в файле vsshell80.idl) в реализации элемента проекта. Это вызывает элемента проекта VSPackage для автоматической загрузки, если оболочка Visual Studio определяет, что система проектов находится в процессе обновления.

2. Уведомить <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> интерфейс через <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> метод.

3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> Интерфейс срабатывает после реализации системы проекта завершении обновления и создается новый обновленный проект. В зависимости от сценария <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> интерфейс срабатывает после <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>, или <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> методы.

### <a name="to-upgrade-the-project-item-files"></a>Чтобы обновить файлы элементов проекта

1. Необходимо тщательно управлять процесс резервного копирования файла в реализации элемента проекта. Это относится, в частности, для резервного копирования side-by-side, где `fUpgradeFlag` параметр <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> задан метод <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP>, куда помещаются файлы, которые созданы резервные копии вдоль стороны файлы, которые обозначены как «расширения» OLD. Старше системное время, когда проект был обновлен файла резервной копии может быть назначен как устаревший. Кроме того они могут быть перезаписаны, если только вы выполнить определенные действия, чтобы избежать этого.

2. Во время вашего элемента проекта получает уведомление о обновления проекта, **мастера преобразования Visual Studio** по-прежнему отображается. Таким образом, следует использовать методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> интерфейс для предоставления сообщений обновления пользовательского интерфейса мастера.

## <a name="see-also"></a>См. также

- [Проекты](../../extensibility/internals/projects.md)
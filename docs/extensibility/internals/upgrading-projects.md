---
title: Модернизация проектов Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9170532746dfc61cdec6636fb669676a94535de1
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301629"
---
# <a name="upgrading-projects"></a>Обновление проектов

Изменения в модели проекта от одной версии Visual Studio к другой могут потребовать обновления проектов и решений, чтобы они могли работать на новой версии. Предоставляет [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] интерфейсы, которые могут быть использованы для реализации поддержки обновления в ваших собственных проектах.

## <a name="upgrade-strategies"></a>Стратегии обновления

Для поддержки обновления реализация проектной системы должна определить и реализовать стратегию обновления. При определении стратегии можно поддерживать резервное копирование постороннике (SxS), копировать резервное копирование или и то, и другое.

- Резервное копирование SxS означает, что проект копирует только те файлы, которые нуждаются в обновлении на месте, добавляя подходящий суффикс имени файла, например, ".старый".

- Копирование резервного копирования означает, что проект копирует все элементы проекта в место ожидания, предоставленное пользователем. Затем соответствующие файлы в исходном месте проекта обновляются.

## <a name="how-upgrade-works"></a>Как работает обновление

Когда решение, созданное в более ранней версии Visual Studio, открывается в новой версии, IDE проверяет файл решения, чтобы определить, нужно ли его модернизировать. При необходимости обновления **мастер обновления** автоматически запускается, чтобы пройти пользователя через процесс обновления.

Когда решение нуждается в обновлении, оно запрашивает у каждого завода проекта свою стратегию обновления. Стратегия определяет, поддерживает ли фабрика проекта резервное копирование копий или резервное копирование SxS. Информация отправляется **в Upgrade Wizard,** который собирает информацию, необходимую для резервного копирования, и представляет применимые варианты пользователю.

### <a name="multi-project-solutions"></a>Многопроектные решения

Если решение содержит несколько проектов и стратегии обновления отличаются, например, когда проект СЗ, который поддерживает только резервное копирование SxS, и веб-проект, который поддерживает только резервное копирование, заводы проекта должны согласовать стратегию обновления.

Решение запрашивает каждый <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>проект завода для . Затем он <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> призывает узнать, нуждаются ли глобальные файлы проекта в обновлении, и определить поддерживаемые стратегии обновления. Затем вызывается **мастер обновления.**

После того, как пользователь <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> завершает мастер, вызывается на каждую фабрику проектов для выполнения фактического обновления. Для облегчения резервного копирования методы IVsProjectUpgradeViaFactory предоставляют <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> службе регистрацию деталей процесса обновления. Эта услуга не может быть кэширована.

После обновления всех соответствующих глобальных файлов, каждая фабрика проекта может выбрать моменттизировать проект. Реализация проекта должна <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>поддерживаться. Затем <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> метод вызывается для обновления всех соответствующих элементов проекта.

> [!NOTE]
> Метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> не предоставляет услугу SVsUpgradeLogger. Эту услугу можно получить, позвонив. <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>

## <a name="best-practices"></a>Рекомендации

Используйте <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> службу, чтобы проверить, можно ли редактировать файл перед его редактированием, и можете сохранить его, прежде чем сохранить его. Это поможет вашей резервной и обновленной реализации обрабатывать файлы проекта под контролем источника, файлы с недостаточным ит-таки.

Используйте <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> службу на всех этапах резервного копирования и обновления, чтобы предоставить информацию об успешном или сбое процесса обновления.

Для получения дополнительной информации о резервном копировании и модернизации проектов, смотрите комментарии для IVsProjectUpgrade в vsshell2.idl.

## <a name="upgrading-custom-projects"></a><a name="upgrading-custom-projects"></a>Модернизация пользовательских проектов

Если вы изменяете данные, сохраненные в файле проекта, при переводе продукта с одной версии Visual Studio на другую, то вам необходимо обеспечить обновление файла проекта со старой версии до новой. Для поддержки обновления, что позволяет участвовать в <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Visual Studio Преобразования **мастера**, реализовать интерфейс. Этот интерфейс содержит единственный доступный метод для обновления копии. Обновление проекта происходит в процессе открытия решения. Интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> реализуется фабрикой проектов или по крайней мере должен получаться из нее.

Старый механизм, предполагающий использование интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, по-прежнему поддерживается, но по сути обновляет систему проекта в процессе открытия проекта. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Интерфейс вызывается средой Visual Studio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> даже если интерфейс называется или реализован. Такой подход позволяет использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> для реализации обновления с копированием только для частей проекта, а остальную работу выполнять на месте (возможно, в новом расположении) с помощью интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

Для реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>выборки [см.](https://github.com/Microsoft/VSSDK-Extensibility-Samples)

При обновлении проектов возникают описанные ниже ситуации.

- Если файл имеет более новый формат, который не поддерживается проектом, то должна возникать соответствующая ошибка. Это предполагает, что старая версия продукта включает код для проверки версии.

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

Если ваша проектная <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> система реализуеттолько только, она не может участвовать в **Visual Studio Conversion Wizard.** Однако даже если вы реализуете интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, вы все же можете задействовать реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> для обновления файлов.

#### <a name="to-implement-ivsprojectupgrade"></a>Реализация интерфейса IVsProjectUpgrade

1. Когда пользователь пытается открыть проект, метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> вызывается средой сразу после открытия проекта. Любые действия пользователя с проектом могут совершаться только после выполнения этого метода. Если пользователь уже получил запрос на обновление решения, флаг <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> передается в параметре `grfUpgradeFlags`. Если пользователь открывает проект напрямую, например, используя команду <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> Add Existing **Project,** флаг не передается, и проект должен побудить пользователя обновиться.

2. В ответ на вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> проект должен определить, должен ли обновляться файл проекта. Если тип проекта не нужно обновлять до новой версии, то проект может просто вернуть флаг <xref:Microsoft.VisualStudio.VSConstants.S_OK>.

3. Если тип проекта нужно обновить до новой версии, следует определить, можно ли изменить файл проекта, вызвав метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> и передав значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> для параметра `rgfQueryEdit`. Затем проекту необходимо выполнить указанные ниже действия.

    - Если значение `VSQueryEditResult`, возвращаемое в параметре `pfEditCanceled`, равно <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>, обновление может продолжаться, так как запись в файл проекта возможна.

    - Если значение `VSQueryEditResult`, возвращаемое в параметре `pfEditCanceled`, равно <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> и в значении `VSQueryEditResult` задан бит <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc>, то метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> должен вернуть ошибку, так как пользователи должны решить проблему с разрешениями самостоятельно. После этого проект должен выполнить следующее действие:

         Сообщите об ошибке <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> пользователю, <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> позвонив и верните код ошибки <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>в .

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

- Если вы не обеспечиваете перезагрузку проекта самостоятельно, то для <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>) должно возвращаться значение `false`. В этом случае, прежде чем <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>(QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits) возвращается, среда создает еще один новый экземпляр вашего проекта, например, Project2, следующим образом:

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

Если вы добавляете или управляете элементами внутри проектных систем, которые вы не реализуете, возможно, потребуется принять участие в процессе обновления проекта. Crystal Reports является примером элемента, который может быть добавлен в систему проекта.

Как правило, исполнители элементов проекта хотят использовать уже полностью мгновенный и обновленный проект, потому что им необходимо знать, что такое ссылки на проект и какие другие свойства проекта существуют для принятия решения об обновлении.

### <a name="to-get-the-project-upgrade-notification"></a>Чтобы получить уведомление об обновлении проекта

1. Установите <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> флаг (определенный в vsshell80.idl) в реализации элемента проекта. Это приводит к автоматической загрузке элемента проекта VSPackage, когда оболочка Visual Studio определяет, что проектная система находится в процессе обновления.

2. Консультировать <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> интерфейс с помощью метода.

3. Интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> сражается после того, как реализация проектной системы завершила свою модернизацию и новый обновленный проект создан. В зависимости от <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> сценария, интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>выстрелил <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>после, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> или методы.

### <a name="to-upgrade-the-project-item-files"></a>Обновление файлов элементов проекта

1. Необходимо тщательно управлять процессом резервного копирования файлов при реализации элемента проекта. Это относится, в частности, к резервному `fUpgradeFlag` копированию <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> бок о <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP>бок, где параметр метода устанавливается, где файлы, которые были резервные файлы, размещаются вдоль боковых файлов, которые обозначены как ".старый". Резервные файлы старше системного времени, когда проект был обновлен, могут быть обозначены как устаревшие. Кроме того, они могут быть перезаписаны, если вы не предпримете конкретные шаги, чтобы предотвратить это.

2. В то время, когда элемент проекта получает уведомление об обновлении проекта, **мастер преобразования Visual Studio** по-прежнему отображается. Поэтому следует использовать методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> интерфейса для предоставления обновлений сообщений в интерфейс мастер-класса.

## <a name="see-also"></a>См. также раздел

- [Проекты](../../extensibility/internals/projects.md)

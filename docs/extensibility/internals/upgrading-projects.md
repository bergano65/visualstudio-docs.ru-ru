---
title: Обновление проектов | Документация Майкрософт
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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409127"
---
# <a name="upgrading-projects"></a>Обновление проектов

Изменение модели проекта с одной версии Visual Studio на следующую может потребовать обновления проектов и решений, чтобы они могли работать в более новой версии. [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] предоставляет интерфейсы, которые можно использовать для реализации поддержки обновления в собственных проектах.

## <a name="upgrade-strategies"></a>Стратегии обновления

Для поддержки обновления в реализации системы проектов должна быть определена и реализована стратегия обновления. При определении стратегии можно выбрать поддержку параллельного резервного копирования (SxS), резервного копирования или и того и другого.

- Резервное копирование SxS означает, что проект копирует только те файлы, которые требуют обновления на месте, добавляя подходящий суффикс имени файла, например ". old".

- Копирование резервной копии означает, что проект копирует все элементы проекта в указанное пользователем расположение резервной копии. После этого обновляются соответствующие файлы в исходном расположении проекта.

## <a name="how-upgrade-works"></a>Принцип работы обновления

Если решение, созданное в более ранней версии Visual Studio, открывается в более новой версии, интегрированная среда разработки проверяет файл решения, чтобы определить, нужно ли его обновить. Если требуется обновление, то **Мастер обновления** запускается автоматически, чтобы проанализировать пользователя с помощью процесса обновления.

Когда решение нуждается в обновлении, оно запрашивает стратегию обновления для каждой фабрики проектов. Стратегия определяет, поддерживает ли фабрика проектов резервное копирование и архивацию SxS. Эти сведения отправляются в **Мастер обновления**, который собирает сведения, необходимые для резервного копирования, и предоставляет пользователю соответствующие параметры.

### <a name="multi-project-solutions"></a>Решения для нескольких проектов

Если решение содержит несколько проектов, а стратегии обновления отличаются, например, если C++ проект поддерживает только службу резервного копирования по протоколу SxS и веб-проект, поддерживающий только резервное копирование, фабрики проектов должны согласовать стратегию обновления.

Решение запрашивает у каждой фабрики проектов <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. Затем он вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A>, чтобы узнать, требуется ли обновление глобальных файлов проекта и определить поддерживаемые стратегии обновления. Затем вызывается **Мастер обновления** .

После того как пользователь завершит работу мастера, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> вызывается в каждой фабрике проектов для выполнения фактического обновления. Чтобы упростить резервное копирование, методы Ивспрожектупградевиафактори предоставляют службу <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> для записи в журнал сведений о процессе обновления. Эта служба не может быть кэширована.

После обновления всех соответствующих глобальных файлов каждая фабрика проектов может выбрать экземпляр проекта. Реализация проекта должна поддерживать <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>. Затем вызывается метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> для обновления всех соответствующих элементов проекта.

> [!NOTE]
> Метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> не предоставляет службу Свсупграделогжер. Эту службу можно получить, вызвав <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>.

## <a name="best-practices"></a>Рекомендации

Используйте службу <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>, чтобы проверить, можно ли изменить файл перед его редактированием, а также сохранить его перед сохранением. Это поможет вашим реализациям резервного копирования и обновления управлять файлами проекта в системе управления версиями, файлами с недостаточными разрешениями и т. д.

Используйте службу <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> на всех этапах резервного копирования и обновления, чтобы предоставить сведения об успешном или неуспешном завершении процесса обновления.

Дополнительные сведения о резервном копировании и обновлении проектов см. в комментариях к IVsProjectUpgrade в vsshell2. idl.

## <a name="upgrading-custom-projects"></a>Обновление пользовательских проектов

Если вы изменяете данные, сохраненные в файле проекта, при переводе продукта с одной версии Visual Studio на другую, то вам необходимо обеспечить обновление файла проекта со старой версии до новой. Для поддержки обновления, позволяющего принять участие в **мастере преобразования Visual Studio**, реализуйте интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. Этот интерфейс содержит единственный доступный метод для обновления копии. Обновление проекта происходит в процессе открытия решения. Интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> реализуется фабрикой проектов или по крайней мере должен получаться из нее.

Старый механизм, предполагающий использование интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, по-прежнему поддерживается, но по сути обновляет систему проекта в процессе открытия проекта. Таким образом, интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> вызывается средой Visual Studio, даже если вызывается или реализуется интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. Такой подход позволяет использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> для реализации обновления с копированием только для частей проекта, а остальную работу выполнять на месте (возможно, в новом расположении) с помощью интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

Пример реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>см. в разделе [VSSDK Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

При обновлении проектов возникают описанные ниже ситуации.

- Если файл имеет более новый формат, который не поддерживается проектом, то должна возникать соответствующая ошибка. Предполагается, что более старая версия продукта содержит код для проверки версии.

- Если в методе <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> указан флаг <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>, будет производиться обновление на месте перед открытием проекта.

- Если в методе <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> указан флаг <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>, производится обновление с копированием.

- Если в вызове <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> указан флаг <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>, пользователь получил от среды запрос на обновление файла проекта на месте после открытия проекта. Например, среда предлагает пользователю выполнить обновление, когда он открывает старую версию решения.

- Если в вызове <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> не указан флаг <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>, то вы должны обеспечить вывод запроса на обновление файла проекта.

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

Если система проектов реализует только <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, она не может участвовать в **мастере преобразования Visual Studio**. Однако даже если вы реализуете интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, вы все же можете задействовать реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> для обновления файлов.

#### <a name="to-implement-ivsprojectupgrade"></a>Реализация интерфейса IVsProjectUpgrade

1. Когда пользователь пытается открыть проект, метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> вызывается средой сразу после открытия проекта. Любые действия пользователя с проектом могут совершаться только после выполнения этого метода. Если пользователь уже получил запрос на обновление решения, флаг <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> передается в параметре `grfUpgradeFlags`. Если пользователь открывает проект напрямую, например с помощью команды **Добавить существующий проект** , то флаг <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> не передается и проект должен предложить пользователю выполнить обновление.

2. В ответ на вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> проект должен определить, должен ли обновляться файл проекта. Если тип проекта не нужно обновлять до новой версии, то проект может просто вернуть флаг <xref:Microsoft.VisualStudio.VSConstants.S_OK>.

3. Если тип проекта нужно обновить до новой версии, следует определить, можно ли изменить файл проекта, вызвав метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> и передав значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> для параметра `rgfQueryEdit`. Затем проекту необходимо выполнить указанные ниже действия.

    - Если значение `VSQueryEditResult`, возвращаемое в параметре `pfEditCanceled`, равно <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>, обновление может продолжаться, так как запись в файл проекта возможна.

    - Если значение `VSQueryEditResult`, возвращаемое в параметре `pfEditCanceled`, равно <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> и в значении `VSQueryEditResult` задан бит <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc>, то метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> должен вернуть ошибку, так как пользователи должны решить проблему с разрешениями самостоятельно. После этого проект должен выполнить следующее действие:

         Сообщите пользователю об ошибке, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> и возвращая код ошибки <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> для <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

    - Если значение `VSQueryEditResult` равно <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> и в значении `VSQueryEditResultFlags` задан бит <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc>, то файл проекта следует получить для изменения, вызвав метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>...).

4. Если вызов метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> для файла проекта приводит к получению этого файла для изменения и извлечению последней версии, то проект выгружается и загружается повторно. После создания еще одного экземпляра проекта метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> вызывается повторно. При втором вызове файл проекта можно записать на диск. Рекомендуется, чтобы проект сохранил копию файла проекта в старом формате с расширением OLD, внес необходимые в связи с обновлением изменения, а затем сохранил файл проекта в новом формате. Если на каком-либо этапе процесса обновления происходит сбой, метод должен сообщить об этом, вернув код ошибки <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>. Это приводит к выгрузке проекта в обозревателе решений.

     Важно полностью понимать процесс, который происходит в среде в случае, если вызов метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (с указанием значения ReportOnly) возвращает флаги <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> и <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc>.

5. Пользователь пытается открыть файл проекта.

6. Среда вызывает вашу реализацию метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>.

7. Если метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> возвращает значение `true`, среда вызывает вашу реализацию метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>.

8. Среда вызывает вашу реализацию метода <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> для открытия файла и инициализации объекта проекта, например Project1.

9. Среда вызывает вашу реализацию метода `IVsProjectUpgrade::UpgradeProject` , чтобы определить, необходимо ли обновить файл проекта.

10. Вы вызываете метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> и передаете значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> для параметра `rgfQueryEdit`.

11. Среда возвращает значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> для `VSQueryEditResult`, а в <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> устанавливается бит `VSQueryEditResultFlags`.

12. Ваша реализация интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> вызывает `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>).

Этот вызов может привести к получению новой копии файла проекта для изменения и извлечению последней версии, а также к необходимости перезагрузить файл проекта. На этом этапе происходит одно из двух указанных ниже действий.

- Если вы самостоятельно обеспечиваете перезагрузку проекта, то среда вызывает вашу реализацию метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (VSITEMID_ROOT). Получив этот вызов, перезагрузите первый экземпляр проекта (Project1) и продолжайте обновление файла проекта. Среда определяет, что вы самостоятельно обеспечиваете перезагрузку проекта, если для `true` (<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>) возвращается значение <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>.

- Если вы не обеспечиваете перезагрузку проекта самостоятельно, то для `false` (<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>) должно возвращаться значение <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>. В этом случае, перед <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>(QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits) среда создает еще один экземпляр проекта, например Project2, как показано ниже:

    1. Среда вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> для первого объекта проекта (Project1), переводя его таким образом в неактивное состояние.

    2. Среда вызывает вашу реализацию метода `IVsProjectFactory::CreateProject` , чтобы создать второй экземпляр проекта (Project2).

    3. Среда вызывает вашу реализацию метода `IPersistFileFormat::Load` для открытия файла и инициализации второго объекта проекта (Project2).

    4. Среда вызывает метод `IVsProjectUpgrade::UpgradeProject` второй раз, чтобы определить, следует ли обновить объект проекта. Однако этот вызов выполняется для второго экземпляра проекта (Project2). Это проект, который открыт в решении.

        > [!NOTE]
        > В случае если первый проект (Project1) переведен в неактивное состояние, в результате первого вызова реализации <xref:Microsoft.VisualStudio.VSConstants.S_OK> должно возвращаться значение <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>.

    5. Вы вызываете метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> и передаете значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> для параметра `rgfQueryEdit`.

    6. Среда возвращает значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>, и обновление может продолжаться, так как запись в файл проекта возможна.

В случае сбоя обновления метод <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> должен возвращать значение `IVsProjectUpgrade::UpgradeProject`. Если обновление не требуется или вы решили не производить его, вызов `IVsProjectUpgrade::UpgradeProject` следует рассматривать как холостой. Если возвращается код ошибки <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>, в решение проекта добавляется узел-заполнитель.

## <a name="upgrading-project-items"></a>Обновление элементов проекта

При добавлении элементов или управлении ими в системах проектов, которые не реализуются, может потребоваться участие в процессе обновления проекта. Crystal Reports — это пример элемента, который можно добавить в систему проектов.

Как правило, разработчики элементов проекта хотят использовать уже полностью созданный и обновленный проект, так как им нужно знать, что такое ссылки на проект и какие другие свойства проекта должны принять решение об обновлении.

### <a name="to-get-the-project-upgrade-notification"></a>Получение уведомления об обновлении проекта

1. Установите флаг <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> (определяется в vsshell80. IDL) в реализации элемента проекта. Это приведет к автоматической загрузке пакета VSPackage элемента проекта, когда оболочка Visual Studio определит, что система проектов находится в процессе обновления.

2. Посоветуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> интерфейс с помощью метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A>.

3. Интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> срабатывает после того, как реализация системы проекта завершит операции обновления и будет создан новый обновленный проект. В зависимости от сценария интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> срабатывает после <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>или методов <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A>.

### <a name="to-upgrade-the-project-item-files"></a>Обновление файлов элементов проекта

1. Необходимо тщательно управлять процессом резервного копирования файлов в реализации элемента проекта. Это относится к параллельной резервной копии, где параметру `fUpgradeFlag` метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> присваивается значение <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP>, где файлы, для которых была создана резервная копия, помещаются в файлы параллельных файлов, обозначенные как "Old". Резервные копии файлов старше системного времени, когда проект был обновлен, можно назначить как устаревшие. Кроме того, они могут быть перезаписаны, если не предпринять конкретные меры по предотвращению этого.

2. Когда элемент проекта получает уведомление об обновлении проекта, **Мастер преобразования Visual Studio** по-прежнему отображается. Поэтому следует использовать методы интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> для предоставления сообщений об обновлении пользовательскому интерфейсу мастера.

## <a name="see-also"></a>См. также раздел

- [Проекты](../../extensibility/internals/projects.md)

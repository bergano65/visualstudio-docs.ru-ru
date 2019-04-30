---
title: Обновление пользовательских проектов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- upgrading project systems
- projects [Visual Studio SDK], upgrading
- project system upgrades [Visual Studio]
ms.assetid: 262ada44-7689-44d8-bacb-9c6d33834d4e
caps.latest.revision: 11
manager: jillfra
ms.openlocfilehash: f9d930765a427d32836f464a424b5cd898090ac5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436533"
---
# <a name="upgrading-custom-projects"></a>Обновление пользовательских проектов
Если вы изменяете данные, сохраненные в файле проекта, при переводе продукта с одной версии Visual Studio на другую, то вам необходимо обеспечить обновление файла проекта со старой версии до новой. Для поддержки обновления, в котором позволяет участвовать в **мастера преобразования Visual Studio**, реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> интерфейс. Этот интерфейс содержит единственный доступный метод для обновления копии. Обновление проекта происходит в процессе открытия решения. Интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> реализуется фабрикой проектов или по крайней мере должен получаться из нее.  
  
 Старый механизм, предполагающий использование интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, по-прежнему поддерживается, но по сути обновляет систему проекта в процессе открытия проекта. Поэтому интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> вызывается средой [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], даже если вызывается или реализуется интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. Такой подход позволяет использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> для реализации обновления с копированием только для частей проекта, а остальную работу выполнять на месте (возможно, в новом расположении) с помощью интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
 Для реализации примера <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, см. в разделе [примеры VSSDK](../misc/vssdk-samples.md).  
  
 При обновлении проектов возникают описанные ниже ситуации.  
  
- Если файл имеет более новый формат, который не поддерживается проектом, то должна возникать соответствующая ошибка. При этом предполагается, что в старой версии продукта, например в версии Visual Studio .NET 2003, есть код для проверки версии.  
  
- Если в методе <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> указан флаг <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>, будет производиться обновление на месте перед открытием проекта.  
  
- Если в методе <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> указан флаг <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>, производится обновление с копированием.  
  
- Если в вызове <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> указан флаг <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS>, пользователь получил от среды запрос на обновление файла проекта на месте после открытия проекта. Например, среда предлагает пользователю выполнить обновление, когда он открывает старую версию решения.  
  
- Если в вызове <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> не указан флаг <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS>, то вы должны обеспечить вывод запроса на обновление файла проекта.  
  
     Ниже приведен пример сообщения запроса на обновление.  
  
     "Проект "%1" был создан в старой версии Visual Studio. Если вы откроете его в этой версии Visual Studio, то после этого, возможно, не сможете открыть его в старых версиях Visual Studio. Продолжить и открыть проект?"  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>Реализация интерфейса IVsProjectUpgradeViaFactory  
  
1. Реализуйте методы интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, в частности метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>, в реализации фабрики проектов или обеспечьте возможность вызова этих методов из реализации фабрики проектов.  
  
2. Если в процессе открытия решения необходимо произвести обновление на месте, укажите флаг <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> в качестве параметра `VSPUVF_FLAGS` в реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>.  
  
3. Если в процессе открытия решения необходимо произвести обновление на месте, укажите флаг <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> в качестве параметра `VSPUVF_FLAGS` в реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>.  
  
4. Для шагов 2 и 3 непосредственные действия по обновлению файла с использованием интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> можно реализовать, как описано в приведенном ниже разделе "Реализация интерфейса `IVsProjectUpgade`". Процесс обновления файла можно также реализовать с помощью интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
5. Используйте методы интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> для вывода связанных с обновлением сообщений для пользователя с помощью мастера миграции Visual Studio.  
  
6. Интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> используется для реализации любого типа обновления файлов, которое должно происходить в рамках обновления проекта. Этот интерфейс не вызывается из <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, а предоставляется как механизм для обновления файлов, которые входят в систему проекта, но сведения о которых могут отсутствовать в основной системе проекта. Например, такая ситуация может возникнуть, если связанными с компилятором файлами и свойствами с одной стороны и остальной системой проекта с другой стороны занимаются разные команды разработчиков.  
  
## <a name="ivsprojectupgrade-implementation"></a>Реализация интерфейса IVsProjectUpgrade  
 Если реализует систему проектов <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> , он не может участвовать в **мастера преобразования Visual Studio**. Однако даже если вы реализуете интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, вы все же можете задействовать реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> для обновления файлов.  
  
#### <a name="to-implement-ivsprojectupgrade"></a>Реализация интерфейса IVsProjectUpgrade  
  
1. Когда пользователь пытается открыть проект, метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> вызывается средой сразу после открытия проекта. Любые действия пользователя с проектом могут совершаться только после выполнения этого метода. Если пользователь уже получил запрос на обновление решения, флаг <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> передается в параметре `grfUpgradeFlags`. Если пользователь открывает проект напрямую, таких как с помощью **добавить существующий проект** команды, то <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> флаг не передается и проект должен запрашивать пользователя для обновления.  
  
2. В ответ на вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> проект должен определить, должен ли обновляться файл проекта. Если тип проекта не нужно обновлять до новой версии, то проект может просто вернуть флаг <xref:Microsoft.VisualStudio.VSConstants.S_OK>.  
  
3. Если тип проекта нужно обновить до новой версии, следует определить, можно ли изменить файл проекта, вызвав метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> и передав значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> для параметра `rgfQueryEdit`. Затем проекту необходимо выполнить указанные ниже действия.  
  
   - Если значение `VSQueryEditResult`, возвращаемое в параметре `pfEditCanceled`, равно <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>, обновление может продолжаться, так как запись в файл проекта возможна.  
  
   - Если значение `VSQueryEditResult`, возвращаемое в параметре `pfEditCanceled`, равно <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> и в значении `VSQueryEditResult` задан бит <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags>, то метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> должен вернуть ошибку, так как пользователи должны решить проблему с разрешениями самостоятельно. После этого проект должен выполнить следующее действие:  
  
        сообщить об ошибке пользователю, вызвав метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>, и вернуть код ошибки <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> в интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
   - Если значение `VSQueryEditResult` равно <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> и в значении `VSQueryEditResultFlags` задан бит <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags>, то файл проекта следует получить для изменения, вызвав метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>...).  
  
4. Если вызов метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> для файла проекта приводит к получению этого файла для изменения и извлечению последней версии, то проект выгружается и загружается повторно. После создания еще одного экземпляра проекта метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> вызывается повторно. При втором вызове файл проекта можно записать на диск. Рекомендуется, чтобы проект сохранил копию файла проекта в старом формате с расширением OLD, внес необходимые в связи с обновлением изменения, а затем сохранил файл проекта в новом формате. Если на каком-либо этапе процесса обновления происходит сбой, метод должен сообщить об этом, вернув код ошибки <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>. Это приводит к выгрузке проекта в обозревателе решений.  
  
    Важно полностью понимать процесс, который происходит в среде в случае, если вызов метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (с указанием значения ReportOnly) возвращает флаги <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> и <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags>.  
  
5. Пользователь пытается открыть файл проекта.  
  
6. Среда вызывает вашу реализацию метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>.  
  
7. Если метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> возвращает значение `true`, среда вызывает вашу реализацию метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>.  
  
8. Среда вызывает вашу реализацию метода <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> для открытия файла и инициализации объекта проекта, например Project1.  
  
9. Среда вызывает вашу реализацию метода `IVsProjectUpgrade::UpgradeProject` , чтобы определить, необходимо ли обновить файл проекта.  
  
10. Вы вызываете метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> и передаете значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> для параметра `rgfQueryEdit`.  
  
11. Среда возвращает значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> для `VSQueryEditResult`, а в `VSQueryEditResultFlags` устанавливается бит <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags>.  
  
12. Ваша реализация интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> вызывает `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>).  
  
    Этот вызов может привести к получению новой копии файла проекта для изменения и извлечению последней версии, а также к необходимости перезагрузить файл проекта. На этом этапе происходит одно из двух указанных ниже действий.  
  
- Если вы самостоятельно обеспечиваете перезагрузку проекта, то среда вызывает вашу реализацию метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (VSITEMID_ROOT). Получив этот вызов, перезагрузите первый экземпляр проекта (Project1) и продолжайте обновление файла проекта. Среда определяет, что вы самостоятельно обеспечиваете перезагрузку проекта, если для <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>) возвращается значение `true`.  
  
- Если вы не обеспечиваете перезагрузку проекта самостоятельно, то для <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>) должно возвращаться значение `false`. В этом случае перед <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>([QEF_ForceEdit_NoPrompting](assetId:///T:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags?qualifyHint=False&autoUpgrade=True), [QEF_DisallowInMemoryEdits](assetId:///T:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags?qualifyHint=False&autoUpgrade=True),) возвращает, среда создает еще один экземпляр проекта, например Project2, как выглядит следующим образом:  
  
  1. Среда вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> для первого объекта проекта (Project1), переводя его таким образом в неактивное состояние.  
  
  2. Среда вызывает вашу реализацию метода `IVsProjectFactory::CreateProject` , чтобы создать второй экземпляр проекта (Project2).  
  
  3. Среда вызывает вашу реализацию метода `IPersistFileFormat::Load` для открытия файла и инициализации второго объекта проекта (Project2).  
  
  4. Среда вызывает метод `IVsProjectUpgrade::UpgradeProject` второй раз, чтобы определить, следует ли обновить объект проекта. Однако этот вызов выполняется для второго экземпляра проекта (Project2). Это проект, который открыт в решении.  
  
      > [!NOTE]
      > В случае если первый проект (Project1) переведен в неактивное состояние, в результате первого вызова реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> должно возвращаться значение <xref:Microsoft.VisualStudio.VSConstants.S_OK>. Реализацию метода [IVsProjectUpgrade::UpgradeProject](http://msdn.microsoft.com/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) см. в разделе `IVsProjectUpgrade::UpgradeProject`.  
  
  5. Вы вызываете метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> и передаете значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> для параметра `rgfQueryEdit`.  
  
  6. Среда возвращает значение <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>, и обновление может продолжаться, так как запись в файл проекта возможна.  
  
  В случае сбоя обновления метод `IVsProjectUpgrade::UpgradeProject` должен возвращать значение <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>. Если обновление не требуется или вы решили не производить его, вызов `IVsProjectUpgrade::UpgradeProject` следует рассматривать как холостой. Если возвращается код ошибки <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>, в решение проекта добавляется узел-заполнитель.  
  
## <a name="see-also"></a>См. также  
 [Мастер преобразования Visual Studio](http://msdn.microsoft.com/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Обновление элементов проекта](../misc/upgrading-project-items.md)   
 [Проекты](../extensibility/internals/projects.md)
---
title: Часто задаваемые вопросы по отладке моментальных снимков | Документация Майкрософт
ms.date: 11/07/2017
ms.topic: reference
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 43b76ad81a2c075a11ff55dcbd7fbc5e8a4b3fe7
ms.sourcegitcommit: ba5e072c9fedeff625a1332f22dcf3644d019f51
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66431850"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Вопросы и ответы по отладке моментальных снимков в Visual Studio

Ниже приведен список вопросов, связанных с отладкой работающих приложений Azure с помощью Snapshot Debugger.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>Как выполнение моментальных снимков влияет на производительность?

Когда для выполнения моментальных снимков приложения используется Snapshot Debugger, он блокирует процесс приложения и приостанавливает ответвленную копию. При отладке моментального снимка вы выполняете отладку в ответвленной копии процесса. Это занимает 10–20 мс. Данный процесс не копирует полных сведений о приложении. Вместо этого он копирует только таблицу страниц и присваивает страницам атрибуты копирования при записи. Если некоторые объекты приложения, которые находятся в куче, будут изменены, то будут скопированы те страницы, которые им соответствуют. Таким образом, каждый из моментальных снимков занимает мало места в памяти (для большинства приложений этот размер соответствует порядка сотни килобайт).

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>Что произойдет при работе с масштабной Службой приложений Azure (несколькими экземплярами приложения)?

При наличии нескольких экземпляров приложения точки моментальных снимков будут применены к каждому из них. А моментальный снимок будет создан только в той точке моментальных снимков, которая первой будет соответствовать всем условиям. Для создания последующих моментальных снимков при наличии нескольких точек моментальных снимков будет использоваться тот же экземпляр, из которого создавался первый моментальный снимок. Точки ведения журнала, отправленные в окно вывода, отобразят сообщения только для одного экземпляра, в то время как точки ведения журнала, отправленные в журналы приложений, отправят сообщения из каждого экземпляра.

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>Как выполняется загрузка символов в Snapshot Debugger?

Для работы расширения Snapshot Debugger требуются соответствующие символы приложения, которые должны быть развернуты в Службе приложений Azure или находиться на локальном компьютере. (Внедренные PDB-файлы сейчас не поддерживаются.) Snapshot Debugger выполнит загрузку символов из Службы приложений Azure автоматически. Начиная с Visual Studio 2017 версии 15.2, при развертывании в Службе приложений Azure также будут развернуты символы вашего приложения.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>Работает ли Snapshot Debugger в сборках выпуска приложения?

Да. Snapshot Debugger предназначен для работы в сборках выпуска. Когда точка моментальных снимков помещается в функцию, она перекомпилируется до отладочной версии, что делает ее доступной для отладки. Остановка работы Snapshot Debugger приведет к возвращению функции к версии сборки выпуска.

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>Могут ли точки ведения журнала привести к побочным эффектам в рабочем приложении?

Нет. Любые сообщения журнала, добавленные в приложение, оцениваются виртуально. Они не создают побочных эффектов в приложении. Тем не менее некоторые из их свойств могут быть недоступны при использовании точек ведения журнала.

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>Работает ли Snapshot Debugger, когда сервер находится под нагрузкой?

Да, он может работать, когда сервер находится под нагрузкой. Snapshot Debugger выполняет проверку, и в ситуации, когда на сервере отсутствует свободная память, он не делает моментальных снимков.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>Как выполнить удаление Snapshot Debugger?

Чтобы удалить расширение сайта Snapshot Debugger в Службе приложений, выполните следующие действия.

1. Отключите службу приложений с помощью Cloud Explorer в Visual Studio или портала Azure.
1. Последовательно перейдите к сайту Kudu Службы приложений (то есть yourappservice.**scm**.azurewebsites.net), а затем к пункту **Расширения сайта**.
1. Чтобы его удалить, в расширении сайта Snapshot Debugger нажмите кнопку со значком "X".

#### <a name="why-are-ports-opened-during-a-snapshot-debugger-session"></a>Почему во время сеанса Snapshot Debugger открываются порты?

Чтобы выполнить отладку моментальных снимков, сделанных в Azure, расширению Snapshot Debugger необходимо открыть набор портов. Это те же порты, которые требуются для удаленной отладки. Список портов приведен в [этой](../debugger/remote-debugger-port-assignments.md) статье.

#### <a name="how-do-i-disable-the-remote-debugger-extension"></a>Как отключить расширение удаленного отладчика?

Для служб приложений:
1. Отключите расширение удаленного отладчика через портал Azure для службы приложений.
2. Портал Azure > колонка ресурсов вашей службы приложений > *параметры приложения*
3. Перейдите к *Отладка* раздела и нажмите кнопку *Off* кнопку для *удаленной отладки*.

Для AKS:
1. Обновление Dockerfile для удаления в разделах, соответствующих [отладчик моментальных снимков Visual Studio на образы Docker](https://github.com/Microsoft/vssnapshotdebugger-docker).
2. Перестройте и повторно разверните измененный образ Docker.

Для масштабирования виртуальных машин и виртуальных машин наборы удалите пулы KeyVaults и NAT для входящего Трафика удаленного отладчика расширения, сертификаты, следующим образом:

1. Удалите расширение удаленного отладчика  

   Чтобы отключить удаленный отладчик для виртуальных машин и масштабируемых наборов виртуальных машин несколькими способами:  

      - Отключить удаленный отладчик с помощью Cloud Explorer  

         - Cloud Explorer > ресурс виртуальной машины > Отключить отладку (отключение отладки не существует для масштабируемого набора в Cloud Explorer виртуальных машин).  


      - Отключить удаленный отладчик с помощью сценариев и командлетов PowerShell  

         Для виртуальной машины:  

         ```
         Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger  
         ```

         Для масштабируемых наборов виртуальных машин:  
         ```
         $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName  
         $extension = $vmss.VirtualMachineProfile.ExtensionProfile.Extensions | Where {$_.Name.StartsWith('VsDebuggerService')} | Select -ExpandProperty Name  
         Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name $extension  
         ```

      - Отключение удаленного отладчика на портале Azure
         - Портал Azure > колонка ресурсов задает виртуальной машины или виртуальные машины масштабируемого > расширения  
         - Удалить расширение Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger  


         > [!NOTE]
         > Масштабируемые наборы виртуальных машин — портал не поддерживает удаление DebuggerListener порты. Необходимо будет использовать Azure PowerShell. Дополнительные сведения см. далее.
  
2. Удаление сертификатов и хранилище ключей Azure

   При установке расширения удаленного отладчика для виртуальной машины или масштабируемые наборы виртуальных машин, для проверки подлинности клиента VS с Azure виртуальные машины создаются сертификаты клиента и сервера/масштабируемых наборов виртуальных машин ресурсы.  

   - Сертификат клиента  

      Этот сертификат является самозаверяющий сертификат, находящийся в хранилище сертификатов: / CurrentUser/My /  

      ```
      Thumbprint                                Subject  
      ----------                                -------  

      1234123412341234123412341234123412341234  CN=ResourceName  
      ```

      — Один из способов удалить этот сертификат с компьютера с помощью PowerShell

      ```
      $ResourceName = 'ResourceName' # from above  
      Get-ChildItem -Path Cert:\CurrentUser\My | Where-Object {$_.Subject -match $ResourceName} | Remove-Item  
      ```

   - Сертификат сервера
      - Соответствующий отпечаток сертификата сервера развертывается как секрет в хранилище ключей Azure. VS попытается найти или создать хранилище ключей с префиксом MSVSAZ * в регион, соответствующий виртуальной машины или масштабируемые наборы виртуальных машин ресурсов. Все виртуальные машины или виртуальной машине масштабируемые наборы ресурсов, развернутых в этом регионе таким образом будут совместно использовать одного хранилища Key Vault.  
      - Чтобы удалить секрет отпечаток сертификата сервера, перейдите на портал Azure и найти хранилище ключей MSVSAZ * в том же регионе, на котором размещается ваш ресурс. Удаление секрета, который требуется создать метки `remotedebugcert<<ResourceName>>`  
      - Также необходимо будет удалить секрет сервера из ресурса с помощью PowerShell.  

      Для виртуальных машин:  

      ```
      $vm.OSProfile.Secrets[0].VaultCertificates.Clear()  
      Update-AzVM -ResourceGroupName $rgName -VM $vm  
      ```
                        
      Для масштабируемых наборов виртуальных машин:  

      ```
      $vmss.VirtualMachineProfile.OsProfile.Secrets[0].VaultCertificates.Clear()  
      Update-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName -VirtualMachineScaleSet $vmss  
      ```
                        
3. Удалите все пулы NAT для входящего Трафика DebuggerListener (масштабируемый набор виртуальных машин только)  

   Удаленный отладчик вводит пулы NAT входящие DebuggerListener, которые применяются к подсистеме балансировки нагрузки в масштабируемом наборе.  

   ```
   $inboundNatPools = $vmss.VirtualMachineProfile.NetworkProfile.NetworkInterfaceConfigurations.IpConfigurations.LoadBalancerInboundNatPools  
   $inboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null  
                
   if ($LoadBalancerName)  
   {
      $lb = Get-AzLoadBalancer -ResourceGroupName $ResourceGroup -name $LoadBalancerName  
      $lb.FrontendIpConfigurations[0].InboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null  
      Set-AzLoadBalancer -LoadBalancer $lb  
   }
   ```

#### <a name="how-do-i-disable-snapshot-debugger"></a>Как отключить отладчик моментальных снимков?

Для службы приложений:
1. Отключите отладчик моментальных снимков на портале Azure для службы приложений.
2. Портал Azure > колонка ресурсов вашей службы приложений > *параметры приложения*
3. Удалить следующие параметры приложения на портале Azure и сохраните изменения. 
    - INSTRUMENTATIONENGINE_EXTENSION_VERSION
    - SNAPSHOTDEBUGGER_EXTENSION_VERSION

    > [!WARNING]
    > Все изменения параметров приложения будет инициировать перезапуск приложения. Дополнительные сведения о параметрах приложения [здесь](https://docs.microsoft.com/azure/app-service/web-sites-configure#app-settings). 

Для AKS:
1. Обновление Dockerfile для удаления в разделах, соответствующих [отладчик моментальных снимков Visual Studio на образы Docker](https://github.com/Microsoft/vssnapshotdebugger-docker).
2. Перестройте и повторно разверните измененный образ Docker.

Для масштабируемых наборов виртуальных машин и виртуальных машин:

Существует несколько способов, чтобы отключить отладчик моментальных снимков:
- Cloud Explorer > виртуальной машины или виртуальные машины масштабируемого набора ресурсов > отключить диагностику

- Портал Azure > виртуальной машины или виртуальные машины масштабируемого набора колонки ресурсов > расширения > Microsoft.Insights.VMDiagnosticsSettings удалить расширение

- Командлеты PowerShell из [Az PowerShell](https://docs.microsoft.com/powershell/azure/overview)

    Виртуальная машина:
    ```
        Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.Insights.VMDiagnosticsSettings 
    ```
    
    Масштабируемые наборы виртуальных машин:
    ```
        $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
        Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name Microsoft.Insights.VMDiagnosticsSettings
    ```

## <a name="see-also"></a>См. также

- [Отладка в Visual Studio](../debugger/index.md)
- [Отладка работающих приложений ASP.NET, с помощью отладчика моментальных снимков](../debugger/debug-live-azure-applications.md)
- [Отладка динамического масштабируемых наборов виртуальных машин Machines\Virtual ASP.NET Azure, с помощью отладчика моментальных снимков](../debugger/debug-live-azure-virtual-machines.md)
- [Отладка с помощью отладчика моментальных снимков Kubernetes динамической ASP.NET в Azure](../debugger/debug-live-azure-kubernetes.md)
- [Устранение неполадок и известные проблемы для отладки моментальных снимков](../debugger/debug-live-azure-apps-troubleshooting.md)
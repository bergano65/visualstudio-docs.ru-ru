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
ms.openlocfilehash: ceda2dd4e85c8db5b66ef753a748977204b8caab
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71211210"
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

1. Отключите службу приложений либо с помощью Cloud Explorer в Visual Studio, либо в портал Azure.
1. Последовательно перейдите к сайту Kudu Службы приложений (то есть yourappservice.**scm**.azurewebsites.net), а затем к пункту **Расширения сайта**.
1. Чтобы его удалить, в расширении сайта Snapshot Debugger нажмите кнопку со значком "X".

#### <a name="why-are-ports-opened-during-a-snapshot-debugger-session"></a>Почему во время сеанса Snapshot Debugger открываются порты?

Чтобы выполнить отладку моментальных снимков, сделанных в Azure, расширению Snapshot Debugger необходимо открыть набор портов. Это те же порты, которые требуются для удаленной отладки. Список портов приведен в [этой](../debugger/remote-debugger-port-assignments.md) статье.

#### <a name="how-do-i-disable-the-remote-debugger-extension"></a>Разделы справки отключить расширение удаленного отладчика?

Для служб приложений:
1. Отключите расширение удаленного отладчика с помощью портал Azure для службы приложений.
2. Портал Azure > колонку ресурсов службы приложений > *Параметры приложения*
3. Перейдите к разделу *Отладка* и нажмите кнопку *Off (выкл* .) для *удаленной отладки*.

Для AKS:
1. Обновите Dockerfile, чтобы удалить разделы, соответствующие [Visual Studio snapshot Debugger в образах DOCKER](https://github.com/Microsoft/vssnapshotdebugger-docker).
2. Перестройте и повторно разверните измененный образ DOCKER.

Для виртуальных машин или масштабируемых наборов виртуальных машин удалите расширения удаленного отладчика, сертификаты, KeyVaults и входящие пулы NAT, как показано ниже.

1. Удалить расширение удаленного отладчика

   Существует несколько способов отключения удаленного отладчика для виртуальных машин и масштабируемых наборов виртуальных машин.

      - Отключение удаленного отладчика с помощью Cloud Explorer

         - Cloud Explorer > ресурсе виртуальной машины > отключить отладку (для масштабируемого набора виртуальных машин на Cloud Explorer не существует отладки).

      - Отключение удаленного отладчика с помощью скриптов и командлетов PowerShell

         Для виртуальной машины:

         ```powershell
         Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger
         ```

         Для масштабируемых наборов виртуальных машин:

         ```powershell
         $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
         $extension = $vmss.VirtualMachineProfile.ExtensionProfile.Extensions | Where {$_.Name.StartsWith('VsDebuggerService')} | Select -ExpandProperty Name
         Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name $extension
         ```

      - Отключение удаленного отладчика с помощью портал Azure
         - Портал Azure > колонки ресурсов для виртуальных машин или масштабируемых наборов виртуальных машин > расширения
         - Удаление расширения Microsoft. VisualStudio. Azure. RemoteDebug. Всремотедебугжер

         > [!NOTE]
         > Масштабируемые наборы виртуальных машин. портал не допускает удаление портов Дебугжерлистенер. Вам потребуется использовать Azure PowerShell. Дополнительные сведения см. далее.

2. Удаление сертификатов и Azure KeyVault

   При установке расширения удаленного отладчика для виртуальных машин или масштабируемых наборов виртуальных машин создаются сертификаты клиента и сервера для проверки подлинности клиента VS с помощью ресурсов виртуальных машин или масштабируемых наборов виртуальных машин Azure.

   - Сертификат клиента

      Это самозаверяющий сертификат, расположенный в CERT:/CurrentUser/My/

      ```
      Thumbprint                                Subject
      ----------                                -------

      1234123412341234123412341234123412341234  CN=ResourceName
      ```

      Один из способов удалить этот сертификат с компьютера — с помощью PowerShell.

      ```powershell
      $ResourceName = 'ResourceName' # from above
      Get-ChildItem -Path Cert:\CurrentUser\My | Where-Object {$_.Subject -match $ResourceName} | Remove-Item
      ```

   - Сертификат сервера
      - Соответствующий отпечаток сертификата сервера развертывается в качестве секрета в Azure KeyVault. VS попытается найти или создать KeyVault с префиксом МСВСАЗ * в регионе, соответствующем ресурсу виртуальной машины или масштабируемого набора виртуальных машин. Все ресурсы виртуальных машин или масштабируемых наборов виртуальных машин, развернутых в этом регионе, будут совместно использовать один и тот же KeyVault.
      - Чтобы удалить секрет отпечатка сертификата сервера, перейдите на портал Azure и найдите МСВСАЗ * KeyVault в том же регионе, где размещен ресурс. Удалить секрет, который должен быть помечен`remotedebugcert<<ResourceName>>`
      - Кроме того, необходимо удалить секрет сервера из ресурса с помощью PowerShell.

      Для виртуальных машин:

      ```powershell
      $vm.OSProfile.Secrets[0].VaultCertificates.Clear()
      Update-AzVM -ResourceGroupName $rgName -VM $vm
      ```

      Для масштабируемых наборов виртуальных машин:

      ```powershell
      $vmss.VirtualMachineProfile.OsProfile.Secrets[0].VaultCertificates.Clear()
      Update-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName -VirtualMachineScaleSet $vmss
      ```

3. Удалить все пулы NAT для входящего трафика Дебугжерлистенер (только для масштабируемых наборов виртуальных машин)

   Удаленный отладчик вводит Дебугжерлистенер пулы NAT, которые применяются к подсистеме балансировки нагрузки масштабируемого набора.

   ```powershell
   $inboundNatPools = $vmss.VirtualMachineProfile.NetworkProfile.NetworkInterfaceConfigurations.IpConfigurations.LoadBalancerInboundNatPools
   $inboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null

   if ($LoadBalancerName)
   {
      $lb = Get-AzLoadBalancer -ResourceGroupName $ResourceGroup -name $LoadBalancerName
      $lb.FrontendIpConfigurations[0].InboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null
      Set-AzLoadBalancer -LoadBalancer $lb
   }
   ```

#### <a name="how-do-i-disable-snapshot-debugger"></a>Разделы справки Отключить Snapshot Debugger?

Для службы приложений:
1. Отключите Snapshot Debugger через портал Azure для службы приложений.
2. Портал Azure > колонку ресурсов службы приложений > *Параметры приложения*
3. Удалите следующие параметры приложения в портал Azure и сохраните изменения.
   - INSTRUMENTATIONENGINE_EXTENSION_VERSION
   - SNAPSHOTDEBUGGER_EXTENSION_VERSION

   > [!WARNING]
   > Любые изменения параметров приложения запустит перезапуск приложения. Дополнительные сведения о параметрах приложения см. [в разделе Настройка приложения службы приложений на портал Azure](/azure/app-service/web-sites-configure).

Для AKS:
1. Обновите Dockerfile, чтобы удалить разделы, соответствующие [Visual Studio snapshot Debugger в образах DOCKER](https://github.com/Microsoft/vssnapshotdebugger-docker).
2. Перестройте и повторно разверните измененный образ DOCKER.

Для масштабируемых наборов виртуальных машин или виртуальных машин:

Существует несколько способов отключения Snapshot Debugger.
- Cloud Explorer > ресурсом масштабируемого набора виртуальных машин или виртуальных машин > отключить диагностику

- Портал Azure > в колонке ресурсов масштабируемого набора виртуальных машин или виртуальных машин > расширения > удалить расширение Microsoft. Insights. VMDiagnosticsSettings

- Командлеты PowerShell из [AZ PowerShell](https://docs.microsoft.com/powershell/azure/overview)

   Виртуальная машина:

   ```powershell
      Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.Insights.VMDiagnosticsSettings
   ```

   Масштабируемые наборы виртуальных машин:

   ```powershell
      $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
      Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name Microsoft.Insights.VMDiagnosticsSettings
   ```

## <a name="see-also"></a>См. также

- [Отладка в Visual Studio](../debugger/index.yml)
- [Отладка динамических ASP.NET приложений с помощью Snapshot Debugger](../debugger/debug-live-azure-applications.md)
- [Отладка динамических масштабируемых наборов ASP.NET Azure Virtual Мачинес\виртуал с помощью Snapshot Debugger](../debugger/debug-live-azure-virtual-machines.md)
- [Отладка Live ASP.NET Azure Kubernetes с помощью Snapshot Debugger](../debugger/debug-live-azure-kubernetes.md)
- [Устранение неполадок и известные проблемы при отладке моментальных снимков](../debugger/debug-live-azure-apps-troubleshooting.md)

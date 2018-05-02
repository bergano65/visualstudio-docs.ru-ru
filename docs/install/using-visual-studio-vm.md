---
title: Использование Visual Studio на виртуальной машине Azure
description: Узнайте, как использовать Visual Studio на виртуальной машине Azure.
ms.date: 03/03/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- azure services
- virtual machine; VM
- installation
- visual studio
author: PhilLee-MSFT
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f0c87d482c2bc7ad174f7074091767fb6127bf70
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/20/2018
---
# <a id="top"> </a> Образы Visual Studio в Azure

Применение Visual Studio на предварительно настроенной виртуальной машине Azure — это простой и быстрый способ использования налаженной среды разработки. Образы системы с различными конфигурациями Visual Studio доступны в [Azure Marketplace](https://azuremarketplace.microsoft.com/marketplace/apps?search=%22visual%20studio%202017%22&page=1).

Вы еще не работали в Azure? [Создайте бесплатную учетную запись Azure](https://azure.microsoft.com/free).

## <a name="what-configurations-and-versions-are-available"></a>Доступные конфигурации и версии

Образы большинства последних основных версий (Visual Studio 2017 и Visual Studio 2015) можно найти в Azure Marketplace. Для каждой основной версии доступна исходная версия (RTW) и последние обновленные версии. Каждая из этих версий включает выпуски Visual Studio Enterprise и Visual Studio Community. Эти образы обновляются по крайней мере раз в месяц и включают последние обновления Visual Studio и Windows. Названия образов не изменяются. В описании каждого из них содержится версия установленного продукта и дата выпуска образа.

| Версия выпуска                                              | Выпуски                     |     Версия продукта     |
|:------------------------------------------------------------:|:----------------------------:|:-----------------------:|
| Visual Studio 2017 — последняя версия (15.6)                    |    Enterprise, Community     |      Версия 15.6.4     |
| Visual Studio 2017: последняя предварительная версия (версия 15.7, предварительная версия 3) |    Enterprise, Community     |      Версия 15.7.0     |
|         Visual Studio 2017 — RTW                              |    Enterprise, Community     |      Версия 15.0.10    |
|   Visual Studio 2015 — последняя версия (обновление 3)                      |    Enterprise, Community     |  Версия 14.0.25431.01  |
|         Visual Studio 2015 — RTW                              |             Нет             | Срок действия обслуживания истек |

> [!NOTE]
> В соответствии с политикой обслуживания корпорации Майкрософт обслуживание изначально выпущенной версии Visual Studio 2015 (RTW) завершено. Обновление 3 — это последняя версия семейства продуктов Visual Studio 2015.

Дополнительные сведения см. в статье [Обслуживание продуктов Visual Studio и Team Foundation Server](/visualstudio/productinfo/vs-servicing-vs).

## <a name="what-features-are-installed"></a>Установленные компоненты

Каждый образ содержит рекомендуемый набор компонентов определенного выпуска Visual Studio. Обычно устанавливаются такие компоненты:

* Все доступные рабочие нагрузки, в том числе дополнительные рекомендуемые компоненты каждой рабочей нагрузки.
* Пакеты SDK .NET 4.6.2 и .NET 4.7, Targeting Pack и средства разработчика.
* Visual F#
* Расширение GitHub для Visual Studio
* Инструменты LINQ to SQL.

Ниже приведен пример командной строки, с помощью которой мы устанавливаем Visual Studio при создании образов.

```shell
    vs_enterprise.exe --allWorkloads --includeRecommended --passive ^
       add Microsoft.Net.Component.4.7.SDK ^
       add Microsoft.Net.Component.4.7.TargetingPack ^
       add Microsoft.Net.Component.4.6.2.SDK ^
       add Microsoft.Net.Component.4.6.2.TargetingPack ^
       add Microsoft.Net.ComponentGroup.4.7.DeveloperTools ^
       add Microsoft.VisualStudio.Component.FSharp ^
       add Component.GitHub.VisualStudio ^
       add Microsoft.VisualStudio.Component.LinqToSql
```

Если образы не включают в себя требуемый компонент Visual Studio, сообщите об этом с помощью средства обратной связи (в правом верхнем углу страницы).

## <a name="what-size-vm-should-i-choose"></a>Выбор размера виртуальной машины

Azure предлагает разные размеры виртуальных машин. Так как Visual Studio — это мощное, многопоточное приложение, необходимо использовать виртуальную машину по крайней мере с 2 процессорами и 7 ГБ памяти. Мы рекомендуем следующие размеры виртуальных машин для образов Visual Studio:

   * Standard_D2_v3
   * Standard_D2s_v3
   * Standard_D4_v3
   * Standard_D4s_v3
   * Standard_D2_v2
   * Standard_D2S_v2
   * Standard_D3_v2

Дополнительные сведения о последних размерах виртуальных машин Windows в Azure см. в [этой статье](/azure/virtual-machines/windows/sizes).

Используя Azure, вы всегда можете изменить размер виртуальной машины. Для этого можно подготовить новую виртуальную машину с более подходящим размером или изменить размер существующего экземпляра. Дополнительные сведения см. в статье [Изменение размера виртуальной машины Windows](/azure/virtual-machines/windows/resize-vm).

## <a name="after-the-vm-is-running-whats-next"></a>Что делать после запуска виртуальной машины?

В Visual Studio в Azure применяется модель с использованием собственной лицензии. Так же как и при установке на собственном оборудовании, одним из первых шагов является лицензирование Visual Studio. Чтобы разблокировать Visual Studio, сделайте следующее:
- Войдите с помощью учетной записи Майкрософт, связанной с подпиской Visual Studio.
- Разблокируйте Visual Studio с помощью ключа продукта, предоставленного во время покупки.

Дополнительные сведения см. в статьях [Вход в Visual Studio](../ide/signing-in-to-visual-studio.md) и [Как разблокировать Visual Studio](../ide/how-to-unlock-visual-studio.md).

## <a name="how-do-i-save-the-development-vm-for-future-or-team-use"></a>Как сохранить виртуальную машину разработки для использования в будущем или использования командой?

Спектр сред разработки довольно большой, а создание более сложных сопряжено со значительными расходами. Независимо от конфигурации вашей среды вы можете сохранить или записать настроенную виртуальную машину в качестве базового образа, который в будущем сможете использовать вы или другие члены команды. Загружая новую виртуальную машину, вы можете подготовить ее из базового образа, а не образа Azure Marketplace.

Краткое описание процесса. Запустите средство System Preparation Tool (Sysprep), завершите работу виртуальной машины, а затем запишите *(рис. 1)* ее в качестве образа с помощью пользовательского интерфейса портала Azure. Azure сохраняет `.vhd`-файл образа в выбранную учетную запись хранения. Затем новый образ появится в списке ресурсов подписки в виде ресурса "Образ".

<img src="media/capture-vm.png" alt="Capture an image through the Azure portal’s UI" style="border:3px solid Silver; display: block; margin: auto;"><center>*Рис. 1. Запись образа через пользовательский интерфейс портала Azure.*</center>

Дополнительные сведения см. в статье [Создание управляемого образа универсальной виртуальной машины в Azure](/azure/virtual-machines/windows/capture-image-resource).

> [!IMPORTANT]
> Не забудьте использовать средство Sysprep для подготовки виртуальной машины. Если пропустить этот шаг, Azure не удается подготовить виртуальную машину из образа.

> [!NOTE]
> За хранение некоторых образов может взиматься плата, но эти дополнительные расходы незначительные по сравнению с затратами на повторное создание виртуальной машины с самого начала для каждого члена команды. Например, создание и хранение образа размером 127 ГБ, который может использовать вся ваша команда в течение месяца, стоит несколько долларов США. Но эти затраты незначительные по сравнению со временем, которое потратит каждый сотрудник на создание индивидуальной среды разработки и проверку ее параметров.

Кроме того, для некоторых задач или технологий разработки могут понадобиться дополнительные возможности, например разные конфигурации разработки и возможности поддержки взаимодействия между несколькими компьютерами. С помощью Azure DevTest Labs можно создать _инструкции_ для автоматизации создания требуемого образа. DevTest Labs также можно использовать для управления политиками виртуальных машин команды. Дополнительные сведения о DevTest Labs см. в [руководстве по использованию этой службы для разработчиков](/azure/devtest-lab/devtest-lab-developer-lab).

## <a name="next-steps"></a>Следующие шаги

Теперь, когда вы знаете о предварительно настроенных образах Visual Studio, вы можете создать виртуальную машину:

* [Создание виртуальной машины Windows с помощью портала Azure](/azure/virtual-machines/windows/quick-create-portal)
* [Обзор виртуальных машин Windows в Azure](/azure/virtual-machines/windows/overview)

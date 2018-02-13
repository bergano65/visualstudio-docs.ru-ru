---
title: "Использование Visual Studio на виртуальной машине Azure | Документация Майкрософт"
description: "Узнайте, как использовать Visual Studio на виртуальной машине Azure."
ms.date: 01/30/2018
ms.technology: vs-acquisition
ms.topic: article
helpviewer_keywords:
- azure services
- virtual machine; VM
- installation
- visual studio
author: PhilLee-MSFT
ms.author: phillee
manager: sacalla
ms.workload:
- multiple
ms.openlocfilehash: d8e99965867d5dbc2710d6c56c5b3dc90fc16dc8
ms.sourcegitcommit: 4b4027244b8de25e30b533148804b87321d3e8a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a id="top"> </a> Образы Visual Studio в Azure
Применение Visual Studio на предварительно настроенной виртуальной машине Azure — это самый простой и быстрый способ использования налаженной среды разработки.  Образы системы с различными конфигурациями Visual Studio доступны в [Azure Marketplace](https://portal.azure.com/). Просто загрузите виртуальную машину и приступайте к работе.

Вы еще не работали в Azure? [Создайте бесплатную учетную запись Azure](https://azure.microsoft.com/free).

## <a name="what-configurations-and-versions-are-available"></a>Доступные конфигурации и версии
В Azure Marketplace содержатся образы большинства последних основных версий: Visual Studio 2017 и Visual Studio 2015.  Здесь доступна первоначальная выпущенная версия (RTW) каждой основной версии и последние версии обновлений.  Каждая из этих версий имеет выпуски Visual Studio Enterprise и Visual Studio Community.  Корпорация Майкрософт обновляет эти образы по крайней мере раз в месяц и включает последние обновления Visual Studio и Windows.  Названия образов не изменяются. В описании каждого из них содержится версия установленного продукта и дата выпуска образа.

|               Версия выпуска              |        Выпуски       |     Версия продукта     |
|:------------------------------------------:|:---------------------:|:-----------------------:|
| Visual Studio 2017 г. — последняя версия (15.5) | Enterprise, Community |      Версия 15.5.3     |
|         Visual Studio 2017 — RTW           | Enterprise, Community |      Версия 15.0.7     |
|   Visual Studio 2015 — последняя версия (обновление 3)   | Enterprise, Community |  Версия 14.0.25431.01  |
|         Visual Studio 2015 — RTW           |         Нет          | Срок действия обслуживания истек |

> [!NOTE]
> В соответствии с политикой обслуживания Microsoft срок действия обслуживания изначально выпущенной версии Visual Studio 2015 (RTW) истек.  Таким образом обновление 3 — это последняя версия семейства продуктов Visual Studio 2015.

Дополнительные сведения см. в статье [Обслуживание продуктов Visual Studio и Team Foundation Server](https://www.visualstudio.com/en-us/productinfo/vs-servicing-vs).

## <a name="what-features-are-installed"></a>Установленные компоненты
Каждый образ содержит рекомендуемый набор компонентов определенного выпуска Visual Studio.  Обычно устанавливаются такие компоненты:

* Все доступные рабочие нагрузки, в том числе дополнительные рекомендуемые компоненты этой рабочей нагрузки.
* Пакеты SDK .NET 4.6.2 и .NET 4.7, Targeting Pack и средства разработчика.
* Visual F#
* Расширение GitHub для Visual Studio
* Инструменты LINQ to SQL.

Ниже приведен пример командной строки, с помощью которой мы устанавливаем Visual Studio при создании образов.

```
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
Подготовить новую виртуальную машину легко. Azure предлагает широкий спектр их размеров.  Как и в случае с приобретением любого оборудования, необходимо учитывать баланс между производительностью и стоимостью.  Так как Visual Studio — это мощное, многопоточное приложение, необходимо использовать виртуальную машину с по крайней мере 2 процессорами и 7 ГБ памяти. В Azure эти показатели имеют виртуальные машины таких размеров:

   * Standard_D2_v3
   * Standard_D2s_v3
   * Standard_D4_v3
   * Standard_D4s_v3
   * Standard_D2_v2
   * Standard_D2S_v2
   * Standard_D3_v2

Дополнительные сведения о последних размерах виртуальных машин Windows в Azure см. в [этой статье](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/sizes).

Используя Azure, вы всегда можете изменить размер виртуальной машины по мере необходимости.  Это можно сделать, подготовив новую виртуальную машину с более подходящим размером или изменив размер имеющегося экземпляра.  Дополнительные сведения см. в статье [Изменение размера виртуальной машины Windows](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/resize-vm).

## <a name="after-i-get-the-vm-running-then-what"></a>Действия после запуска виртуальной машины
В Visual Studio в Azure применяется модель с использованием собственной лицензии.  Аналогично установке на собственном оборудовании один из первых шагов заключается в лицензировании Visual Studio.  Разблокировать Visual Studio можно путем входа в систему с учетной записью Майкрософт, связанной с подпиской Visual Studio, или же использовав ключ продукта, полученного при первоначальной покупке.  Дополнительные сведения см. в статьях [Вход в Visual Studio](https://docs.microsoft.com/en-us/visualstudio/ide/signing-in-to-visual-studio) и [Практическое руководство. Разблокирование Visual Studio](https://docs.microsoft.com/en-us/visualstudio/ide/how-to-unlock-visual-studio).

## <a name="after-i-build-out-the-dev-vm-how-do-i-save-capture-it-for-future-or-team-use"></a>Сохранение виртуальной машины для последующей работы

Спектр сред разработки довольно большой, а создание более сложных сопряжено со значительными расходами.  Независимо от конфигурации среды Azure позволяет сократить расходы за счет сохранения настроенной виртуальной машины как базового образа, который можно использовать в будущем самостоятельно или совместно с участниками группы.  Затем при загрузке новой виртуальной машины ее можно подготовить из базового образа, а не образа Marketplace.

Кратко рассмотрим этот процесс. Запустите Sysprep, завершите работу виртуальной машины, а затем *захватите (рис. 1)* ее в качестве образа с помощью пользовательского интерфейса портала Azure.  Azure сохраняет VHD-файл образа в выбранную учетную запись хранения.  Затем новый образ можно просмотреть в списке ресурсов подписки в виде ресурса образа.

<img src="media/capture-vm.png" alt="Capture an image through the Azure portal’s UI" style="border:3px solid Silver; display: block; margin: auto;"><center>*Рис. 1. Запись образа через пользовательский интерфейс портала Azure.*</center>

Дополнительные сведения см. в статье [Create a managed image of a generalized VM in Azure](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/capture-image-resource) (Создание управляемого образа виртуальной машины общего назначения в Azure).

  **Напоминание.** Не забудьте запустить Sysprep на виртуальной машине.  Если пропустить этот шаг, Azure не удается подготовить виртуальную машину из образа.

> [!NOTE]
> За хранение некоторых образов может взиматься плата, но дополнительные расходы незначительные по сравнению с затратами усилий на перестроение виртуальной машины с самого начала для каждого пользователя в группе.  Например, создание и хранение образа размером 127 ГБ, который смогут использовать все пользователи в течение месяца, стоит несколько долларов США.  Тем не менее эти затраты незначительные по сравнению со временем, которое потратит каждый сотрудник на создание индивидуальной среды разработки и проверку ее параметров.

Кроме того, для некоторых задач или технологий разработки могут понадобиться дополнительные возможности, например разные конфигурации разработки и возможности поддержки взаимодействия между несколькими компьютерами.  С помощью Azure DevTest Labs можно создать _инструкции_ для автоматизации создания "окончательного образа" и управления политиками виртуальных машин команды.  Дополнительные сведения о DevTest Labs см. в [руководстве по использованию этой службы для разработчиков](https://docs.microsoft.com/en-us/azure/devtest-lab/devtest-lab-developer-lab).

## <a name="next-steps"></a>Следующие шаги
Узнав о предварительно настроенных образах Visual Studio, вы можете создать виртуальную машину:

* [Создание виртуальной машины Windows с помощью портала Azure](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/quick-create-portal)
* [Обзор виртуальных машин Windows в Azure](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/overview)

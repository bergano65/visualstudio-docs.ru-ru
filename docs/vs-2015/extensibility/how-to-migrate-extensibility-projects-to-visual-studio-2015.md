---
title: Практическое руководство. Перенос проектов расширяемости в Visual Studio 2015 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 41bf80c8ae00aa22666750de7b4b23df981c8465
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435925"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>Практическое руководство. Перенос проектов расширяемости в Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вот как можно обновить расширение.  
  
> [!IMPORTANT]
> Если вы планируете сохранить версию решения расширения для более ранней версии Visual Studio, не забудьте создать копию перед его обновлением. Сложно, чтобы вернуться в предыдущее состояние обновленной версии.  
  
#### <a name="to-upgrade-an-extensibility-solution"></a>Обновление решений расширяемости  
  
1. С помощью копии, необходимо обновить, откройте его в новой версии. Пользователю будет рекомендовано обновления является необратимой.  
  
2. После завершения обновления, измените путь к этой внешней программе до новой версии devenv.exe. Щелкните правой кнопкой мыши узел проекта в **обозревателе решений**, затем выберите **свойства**. В **Отладка** вкладке, найдите текстовое поле с **запуск внешней программы** и измените путь к devenv.exe в Visual Studio 2015 путь, который должен выглядеть следующим образом:  
  
     **%ProgramFiles%\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe**  
  
3. Добавьте ссылку на Microsoft.VisualStudio.Shell.14.0.dll. (Щелкните правой кнопкой мыши узел проекта в **обозревателе решений** и выберите **добавьте / Reference**. Выберите **расширения** вкладку и проверьте **Microsoft.VisualStudio.Shell.14.0**.)  
  
4. Постройте решение. Файлы сборки развертываются для:  
  
     **%LOCALAPPDATA%\Microsoft\VisualStudio.14.0Exp\Extensions\\< создавать имя\>\\< имя проекта\>\\< версия проекта\>\\**.  
  
#### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>Чтобы обновить проект расширяемости NuGet VS SDK ссылаться на сборки  
  
1. Определите VS SDK ссылочные сборки, необходимые для проекта.  В **обозревателе решений**, разверните узел проекта **ссылки** узел и ознакомьтесь со списком ссылок проекта.  Ссылки на сборки VS SDK будет иметь префикс **Microsoft.VisualStudio** в имени (например: Microsoft.VisualStudio.Shell.14.0).  
  
2. Удалить ссылочные сборки VS SDK из проекта, выбрав их, щелкните правой кнопкой мыши и **удалить**.  
  
3. Добавьте версии NuGet ссылочных сборок пакета SDK для VS.  Оставаясь в **ссылки на обозревателе решения** открытым узлом **управление пакетами NuGet...** диалоговое окно.  Если вы хотите узнать больше об этом диалоговом окне, см. в разделе [управление пакетами NuGet с помощью диалогового окна](http://docs.nuget.org/Consume/Package-Manager-Dialog). Ссылочные сборки VS SDK публикуются на [nuget.org](http://www.nuget.org) по [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility).  
  
4. С помощью **nuget.org** как вашей **источник пакета**, найдите имя пакета NuGet, которое совпадает с требуемой базовой сборки (например: Microsoft.VisualStudio.Shell.14.0) и установите его в проект.  NuGet может добавить несколько ссылочных сборок для удовлетворения требований начальной его зависимости.  
  
     При желании можно добавить все ссылочные сборки VS SDK за один раз, установив пакет SDK для VS [метапакет](http://www.nuget.org/packages/VSSDK_Reference_Assemblies).  
  
5. Вы также можете использовать NuGet версии средств сборки пакета SDK для VS. Этот пакет NuGet — это [Microsoft.VSSDK.BuildTools](http://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) и после добавления проекта, содержащих необходимые средства и файлы, чтобы дать вам возможность создавать расширения проекта на компьютере не установлен пакет SDK для VS.  
  
> [!NOTE]
> Это не требуется обновить существующие проекты расширения среды для использования NuGet ссылочных сборок и средства.  Они могут продолжать построение с помощью ссылочных сборок и средств, устанавливаемых с VS SDK.

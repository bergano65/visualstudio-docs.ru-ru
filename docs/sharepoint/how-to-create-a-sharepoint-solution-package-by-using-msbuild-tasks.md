---
title: "Как: Создание пакета решения SharePoint с помощью задач MSBuild | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 210793ab224e4da324591780dd3e6b171a1d721a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>Практическое руководство. Создание пакета решения SharePoint с помощью задач MSBuild
  Сборки, очистки и проверка пакета SharePoint (WSP-файл) с помощью командной строки MSBuild задачи на компьютере разработчика. Эти команды также можно использовать для автоматизации процесса сборки с помощью Team Foundation Server на компьютере построения.  
  
## <a name="building-a-sharepoint-package"></a>Построение пакета SharePoint  
  
#### <a name="to-build-a-sharepoint-package"></a>Для создания пакета SharePoint  
  
1.  В ОС Windows **запустить** меню, выберите **все программы**, **стандартные**, **командной строки**.  
  
2.  Перейдите в каталог, где находится проект SharePoint.  
  
3.  Введите следующую команду, чтобы создать пакет для проекта. Замените *ProjectFileName* с именем проекта.  
  
    ```  
    msbuild /t:Package ProjectFileName  
    ```  
  
     Например можно выполнить одно из следующих команд, чтобы упаковать проект SharePoint с названием ListDefinition1.  
  
    ```  
    msbuild /t:Package ListDefinition1.vbproj  
    msbuild /t:Package ListDefinition1.csproj  
    ```  
  
## <a name="cleaning-a-sharepoint-package"></a>Очистка пакета SharePoint  
  
#### <a name="to-clean-a-sharepoint-package"></a>Чтобы очистить пакет SharePoint  
  
1.  Откройте окно командной строки.  
  
2.  Перейдите в каталог, где находится проект SharePoint.  
  
3.  Введите следующую команду, чтобы очистить пакет для проекта. Замените *ProjectFileName* с именем проекта.  
  
    ```  
    msbuild /t:CleanPackage ProjectFileName  
    ```  
  
     Например можно выполнить одно из следующих команд, чтобы очистить проект SharePoint с названием ListDefinition1.  
  
    ```  
    msbuild /t:CleanPackage ListDefinition1.vbproj  
    msbuild /t:CleanPackage ListDefinition1.csproj  
    ```  
  
## <a name="validating-a-sharepoint-package"></a>Проверка пакета SharePoint  
  
#### <a name="to-validate-a-sharepoint-package"></a>Чтобы проверить пакет SharePoint  
  
1.  Откройте окно командной строки.  
  
2.  Перейдите в каталог, где находится проект SharePoint.  
  
3.  Введите следующую команду, чтобы проверить пакет для проекта. Замените *ProjectFileName* с именем проекта.  
  
    ```  
    msbuild /t:ValidatePackage ProjectFileName  
    ```  
  
     Например можно выполнить одно из следующих команд, чтобы проверить проект SharePoint с названием ListDefinition1.  
  
    ```  
    msbuild /t:ValidatePackage ListDefinition1.vbproj  
    msbuild /t:ValidatePackage ListDefinition1.csproj  
    ```  
  
## <a name="setting-properties-in-a-sharepoint-package"></a>Настройка свойств пакета SharePoint  
  
#### <a name="to-set-a-property-in-a-sharepoint-package"></a>Чтобы задать свойство в пакете SharePoint  
  
1.  Откройте окно командной строки.  
  
2.  Перейдите в каталог, где находится проект SharePoint.  
  
3.  Введите следующую команду, чтобы задать значение свойства в пакет для проекта. Замените *PropertyName* со свойством, которое требуется задать.  
  
    ```  
    msbuild /property:PropertyName=Value  
    ```  
  
     Например можно выполнить следующую команду, чтобы установить уровень предупреждений.  
  
    ```  
    msbuild /property:WarningLevel = 2  
    ```  
  
## <a name="see-also"></a>См. также  
 [Создание компонентов SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Как: Настройка компонента SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Практическое руководство. Добавление и удаление элементов в компонентах SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
  
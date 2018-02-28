---
title: "Как: Настройка пакета решения SharePoint с помощью целевых объектов MSBuild | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: ab9aa26efe3002c28ec031457d2732c828eca445
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets"></a>Практическое руководство. Настройка пакета решения SharePoint с помощью целевых объектов MSBuild
  С помощью целевых объектов MSBuild, управляемых в командной строке, можно настраивать способ создания пакетов SharePoint (WSP-файлов) в Visual Studio. Например, можно настроить свойства MSBuild для изменения промежуточного каталога пакета и группы элементов MSBuild с перечисляемыми файлами.  
  
## <a name="customizing-and-running-msbuild-targets"></a>Настройка и выполнение целевых объектов MSBuild  
 При настройке целевых объектов BeforeLayout и AfterLayout можно выполнять задачи до компоновки пакета, например добавлять, удалять или изменять файлы, которые будут упакованы.  
  
#### <a name="to-customize-the-beforelayout-target"></a>Для настройки целевой BeforeLayout  
  
1.  Откройте текстовый редактор, например Блокнот, и добавьте следующий код.  
  
    ```  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <Target Name="BeforeLayout">  
        <Message Importance="high" Text="In the BeforeLayout Target"></Message>  
      </Target>  
    </Project>  
    ```  
  
     Этот пример выводит сообщение перед упаковкой данного целевого объекта.  
  
2.  Назовите файл **CustomLayout.SharePoint.targets**, а затем сохраните его в папке проекта SharePoint.  
  
3.  Откройте проект, откройте ее контекстное меню и выберите **выгрузить проект**.  
  
4.  В **обозревателе решений**, откройте контекстное меню для проекта и выберите **изменить***ProjectName***.vbproj** или **Изменить***ProjectName***.csproj**.  
  
5.  После строки `Import` в конце файла проекта добавьте следующую строку.  
  
    ```  
    <Import Project="CustomLayout.SharePoint.targets" />  
    ```  
  
6.  Сохраните и закройте файл проекта.  
  
7.  В **обозревателе решений**, откройте контекстное меню для проекта и выберите **перезагрузить проект**.  
  
 При публикации проекта сообщение выведется, прежде чем начнется упаковка.  
  
#### <a name="to-customize-the-afterlayout-target"></a>Для настройки целевой AfterLayout  
  
1.  В строке меню выберите **файл**, **откройте**, **файл**.  
  
2.  В **открыть файл** диалоговое окно, перейдите в папку проекта, выберите файл CustomLayout.target и выберите **откройте** кнопки.  
  
3.  Непосредственно перед тегом `</Project>` добавьте следующий код:  
  
    ```  
    <Target Name="AfterLayout">  
      <Message Importance="high" Text="In the AfterLayout Target"></Message>  
    </Target>  
    ```  
  
     Этот пример выводит сообщение после того, как этот целевой объект упаковывается.  
  
4.  Сохраните и закройте файл targets.  
  
5.  Перезапустите среду Visual Studio и откройте проект.  
  
 При публикации проекта сообщение BeforeLayout выведется, прежде чем начнется упаковка, а сообщение AfterLayout выведется после того, как упаковка завершится.  
  
## <a name="see-also"></a>См. также  
 [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  
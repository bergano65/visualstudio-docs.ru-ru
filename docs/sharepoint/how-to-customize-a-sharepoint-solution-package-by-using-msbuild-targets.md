---
title: "Практическое руководство. Настройка пакета решения SharePoint с помощью целевых объектов MSBuild"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "разработка приложений SharePoint в Visual Studio, пакеты"
ms.assetid: 7fa6a276-04c8-463e-be95-57c2c6240d76
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Практическое руководство. Настройка пакета решения SharePoint с помощью целевых объектов MSBuild
  С помощью целевых объектов MSBuild, управляемых командной строкой, можно настраивать способ создания пакетов SharePoint \(WSP\-файлов\).  Например, можно настроить свойства MSBuild, чтобы изменить промежуточный каталог пакета и группы элементов MSBuild с перечисляемыми файлами.  
  
## Настройка и выполнение целевых объектов MSBuild  
 При настройке целевых объектов BeforeLayout и AfterLayout можно выполнять задачи до компоновки пакета, например добавлять, удалять или изменять файлы, которые будут упакованы.  
  
#### Настройка целевого объекта BeforeLayout  
  
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
  
3.  Откройте проект, откройте его контекстное меню и выберите пункт **Выгрузить проект**.  
  
4.  В **обозревателе решений** откройте контекстное меню для проекта и выберите **Изменить** *ProjectName***.vbproj** или **Изменить** *ProjectName***.csproj**.  
  
5.  После строки `Import` в конце файла проекта добавьте следующую строку.  
  
    ```  
    <Import Project="CustomLayout.SharePoint.targets" />  
    ```  
  
6.  Сохраните и закройте файл проекта.  
  
7.  В **обозревателе решений** откройте контекстное меню для своего проекта и выберите **Перезагрузить проект**.  
  
 При публикации проекта сообщение выведется прежде чем начнется упаковка.  
  
#### Настройка целевого объекта AfterLayout  
  
1.  В строке меню последовательно выберите **Файл**, **Открыть**, **Файл**.  
  
2.  В диалоговом окне **Открыть файл** перейдите к папке проекта, выберите файл CustomLayout.target, а затем нажмите кнопку **Открыть**.  
  
3.  Непосредственно перед тегом `</Project>` добавьте следующий код:  
  
    ```  
    <Target Name="AfterLayout">  
      <Message Importance="high" Text="In the AfterLayout Target"></Message>  
    </Target>  
    ```  
  
     Этот пример выводит сообщение после того, как этот целевой объект упакован.  
  
4.  Сохраните и закройте файл.  
  
5.  Перезапустите среду Visual Studio и откройте проект.  
  
 При публикации проекта сообщение BeforeLayout выведется прежде чем начнется упаковка и сообщение AfterLayout выведется после того, как упаковка завершится.  
  
## См. также  
 [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  
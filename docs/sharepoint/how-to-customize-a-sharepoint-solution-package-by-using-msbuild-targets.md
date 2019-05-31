---
title: Настройка пакета решения SharePoint с помощью целевых объектов MSBuild
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 71665f6ccf22ace264ff39831521538a335aed93
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401512"
---
# <a name="how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets"></a>Практическое руководство. Настройка пакета решения SharePoint с помощью целевых объектов MSBuild
  С помощью целевых объектов MSBuild в командной строке, можно настроить, как Visual Studio создает файлы пакета SharePoint ( *.wsp*). Например, можно настроить свойства MSBuild для изменения промежуточного каталога пакета и группы элементов MSBuild с перечисляемыми файлами.

## <a name="customize-and-run-msbuild-targets"></a>Настройка и выполнение целевых объектов MSBuild
 При настройке целевых объектов BeforeLayout и AfterLayout можно выполнять задачи до компоновки пакета, например добавлять, удалять или изменять файлы, которые будут упакованы.

#### <a name="to-customize-the-beforelayout-target"></a>Для настройки целевых BeforeLayout

1. Откройте текстовый редактор, например Блокнот, и добавьте следующий код.

   ```xml
   <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Target Name="BeforeLayout">
       <Message Importance="high" Text="In the BeforeLayout Target"></Message>
     </Target>
   </Project>
   ```

    Этот пример выводит сообщение перед упаковкой данного целевого объекта.

2. Назовите файл **CustomLayout.SharePoint.targets**, а затем сохраните его в папке проекта SharePoint.

3. Откройте проект, откройте его контекстное меню и выберите **выгрузить проект**.

4. В **обозревателе решений**, откройте контекстное меню для проекта и нажмите кнопку **изменить**  *\<имя_проекта > .vbproj* или **изменить**  *\<Имя_проекта > .csproj*.

5. После строки `Import` в конце файла проекта добавьте следующую строку.

   ```xml
   <Import Project="CustomLayout.SharePoint.targets" />
   ```

6. Сохраните и закройте файл проекта.

7. В **обозревателе решений**, откройте контекстное меню для проекта и нажмите кнопку **перезагрузить проект**.

   При публикации проекта сообщение выведется, прежде чем начнется упаковка.

#### <a name="to-customize-the-afterlayout-target"></a>Для настройки целевых AfterLayout

1. В строке меню выберите **файл** > **откройте** > **файл**.

2. В **открыть файл** диалоговом окне перейдите в папку проекта, выберите файл CustomLayout.target и затем выберите **откройте** кнопки.

3. Непосредственно перед тегом `</Project>` добавьте следующий код:

   ```xml
   <Target Name="AfterLayout">
     <Message Importance="high" Text="In the AfterLayout Target"></Message>
   </Target>
   ```

    Этот пример выводит сообщение после того, как этот целевой объект упаковывается.

4. Сохраните и закройте файл targets.

5. Перезапустите среду Visual Studio и откройте проект.

   При публикации проекта сообщение BeforeLayout выведется, прежде чем начнется упаковка, а сообщение AfterLayout выведется после того, как упаковка завершится.

## <a name="see-also"></a>См. также
- [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)

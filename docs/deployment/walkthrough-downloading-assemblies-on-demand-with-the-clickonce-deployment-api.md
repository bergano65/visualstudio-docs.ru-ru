---
title: "Пошаговое руководство. Загрузка сборок по требованию с помощью API развертывания ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "сборки, загрузка [ClickOnce]"
  - "развертывание ClickOnce, загрузка по требованию"
  - "сборки по требованию, ClickOnce"
ms.assetid: d20e2789-8621-4806-b5b7-841122da1456
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Пошаговое руководство. Загрузка сборок по требованию с помощью API развертывания ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

По умолчанию все сборки, содержащиеся в приложении [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], загружаются при первом запуске приложения.  Однако могут иметься части приложения, которые используются небольшим числом пользователей.  В этом случае необходимо, чтобы сборка загружалась только при создании одного из ее типов.  В следующем разборе примера демонстрируется маркировка определенных сборок в приложении как "необязательных" и их загрузка с помощью классов в пространстве имен <xref:System.Deployment.Application> по запросам общеязыковой среды выполнения.  
  
> [!NOTE]
>  Чтобы использовать эту процедуру, приложение должно выполняться с полным доверием.  
  
## Обязательные компоненты  
 Чтобы выполнить данный разбор примера, потребуется один из следующих компонентов:  
  
-   SDK для Windows.  SDK для Windows можно загрузить с веб\-узла "Центр загрузки Майкрософт".  
  
-   Visual Studio.  
  
## Создание проектов  
  
#### Чтобы создать проект, использующий сборку по требованию  
  
1.  Создайте каталог с именем ClickOnceOnDemand.  
  
2.  Откройте окно командной строки SDK для Windows или окно командной строки [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
3.  Измените каталог на ClickOnceOnDemand.  
  
4.  Создайте пару открытого и закрытого ключей, используя следующую команду:  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5.  Используя Блокнот или другой текстовый редактор, определите класс с именем `DynamicClass`, имеющий единственное свойство с именем `Message`.  
  
     [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]
     [!code-cs[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]  
  
6.  В зависимости от используемого языка сохраните текст как файл с именем `ClickOnceLibrary.cs` или `ClickOnceLibrary.vb` в каталог ClickOnceOnDemand.  
  
7.  Скомпилируйте файл в сборку.  
  
    ```c#  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb#  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8.  Чтобы получить для сборки маркер открытого ключа, выполните следующую команду:  
  
    ```  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. Создайте новый файл, используя текстовый редактор или введя следующий код.  Этот код позволяет создать приложение Windows Forms, которое загружает сборку ClickOnceLibrary, когда она необходима.  
  
     [!code-cs[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.cs)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.vb)]  
  
10. Найдите в коде вызов метода <xref:System.Reflection.Assembly.LoadFile%2A>.  
  
11. Установите для `PublicKeyToken` значение, которое было извлечено раньше.  
  
12. Сохраните файл как `Form1.cs` или `Form1.vb`.  
  
13. Скомпилируйте его в исполняемый файл, воспользовавшись следующей командой.  
  
    ```c#  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb#  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## Пометка сборок как необязательных  
  
#### Чтобы пометить сборки как необязательные в приложении ClickOnce с помощью средства MageUI.exe  
  
1.  Используя MageUI.exe, создайте манифест приложения, как описано в [Разбор примера: развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  Для манифеста приложения используйте следующие параметры:  
  
    -   Назовите манифест приложения как `ClickOnceOnDemand`.  
  
    -   На странице **Файлы** в строке ClickOnceLibrary.dll установите для столбца **Тип файла** значение **Нет**.  
  
    -   На странице **Файлы** в строке ClickOnceLibrary.dll введите `ClickOnceLibrary.dll` в столбец **Группа**.  
  
2.  Используя MageUI.exe, создайте манифест развертывания, как описано в [Разбор примера: развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  Для манифеста развертывания используйте следующие параметры:  
  
    -   Назовите манифест развертывания как `ClickOnceOnDemand`.  
  
## Проверка новой сборки  
  
#### Чтобы проверить сборку по требованию  
  
1.  Передайте развертывание [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] на веб\-сервер.  
  
2.  Запустите приложение, развернутое с помощью [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], из веб\-браузера, введя URL\-адрес в манифест развертывания.  Если вызывается приложение [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] с именем `ClickOnceOnDemand`, и выполняется его передача в корневой каталог веб\-узла adatum.com, URL\-адрес выглядел бы следующим образом:  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3.  Когда появится главная форма, нажмите кнопку <xref:System.Windows.Forms.Button>.  В окне сообщения должна быть видна строка "Hello, World\!".  
  
## См. также  
 <xref:System.Deployment.Application.ApplicationDeployment>
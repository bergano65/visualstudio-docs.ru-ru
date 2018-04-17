---
title: 'Пошаговое руководство: Загрузка сборок по требованию с помощью API развертывания ClickOnce | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: d20e2789-8621-4806-b5b7-841122da1456
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: a9dc200d2dbab68dd3cc4577f5024df4077bfc6a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Пошаговое руководство. Загрузка сборок по требованию с помощью API развертывания ClickOnce
По умолчанию все сборки, включенные в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения загружаются при первом запуске приложения. Однако могут иметь части приложения, которые используются в небольшое количество пользователей. В этом случае рекомендуется скачивать сборку только при создании одного из ее типов. Следующий пример демонстрирует, как пометить определенные сборки в приложении как «необязательные» и их загрузка с помощью классов в <xref:System.Deployment.Application> пространства имен, если они необходимы для общеязыковой среды выполнения (CLR).  
  
> [!NOTE]
>  Для выполнения данной процедуры приложение должно выполняться с полным доверием.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Требуется один из следующих компонентов для выполнения данного пошагового руководства:  
  
-   Пакет Windows SDK. Пакет Windows SDK можно загрузить из центра загрузки Майкрософт.  
  
-   Visual Studio.  
  
## <a name="creating-the-projects"></a>Создание проектов  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>Чтобы создать проект, использующий сборку по запросу  
  
1.  Создайте каталог с именем ClickOnceOnDemand.  
  
2.  Откройте окно командной строки Windows SDK или [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] командной строки.  
  
3.  Перейдите в каталог ClickOnceOnDemand.  
  
4.  Создать пару открытого и закрытого ключей, используя следующую команду:  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5.  С помощью блокнота или другого текстового редактора, определите класс с именем `DynamicClass` с одним свойством `Message`.  
  
     [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]
     [!code-csharp[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]  
  
6.  Сохраните файл с именем `ClickOnceLibrary.cs` или `ClickOnceLibrary.vb`, в зависимости от языка, который используется, в каталог ClickOnceOnDemand.  
  
7.  Этот файл можно Скомпилируйте в сборку.  
  
    ```csharp  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8.  Чтобы получить токен открытого ключа для сборки, используйте следующую команду:  
  
    ```  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. Создать новый файл, используя текстовый редактор и введите следующий код. Этот код создает приложение Windows Forms, который загружает сборки ClickOnceLibrary при необходимости.  
  
     [!code-csharp[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.cs)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.vb)]  
  
10. В коде, найдите вызов <xref:System.Reflection.Assembly.LoadFile%2A>.  
  
11. Задать`PublicKeyToken` значение, которое было извлечено раньше.  
  
12. Сохраните файл как `Form1.cs` или `Form1.vb`.  
  
13. Скомпилируйте его в исполняемый файл с помощью следующей команды.  
  
    ```csharp  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## <a name="marking-assemblies-as-optional"></a>Пометка сборок как необязательных  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>Чтобы пометить сборки как необязательные в приложении ClickOnce с помощью MageUI.exe  
  
1.  С помощью MageUI.exe, создайте манифест приложения, как описано в [Пошаговое руководство: развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Для манифеста приложения, используйте следующие параметры:  
  
    -   Имя манифеста приложения `ClickOnceOnDemand`.  
  
    -   На **файлы** , в строке ClickOnceLibrary.dll задать **тип файла** столбец **нет**.  
  
    -   На **файлы** страницы в тип строки ClickOnceLibrary.dll `ClickOnceLibrary.dll` в **группы** столбца.  
  
2.  С помощью MageUI.exe, создайте манифест развертывания, как описано в [Пошаговое руководство: развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Используйте следующие параметры для манифеста развертывания:  
  
    -   Имя манифеста развертывания `ClickOnceOnDemand`.  
  
## <a name="testing-the-new-assembly"></a>Тестирование новой сборки  
  
#### <a name="to-test-your-on-demand-assembly"></a>Тестирование сборки по запросу  
  
1.  Отправьте ваш [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертывание веб-сервере.  
  
2.  Запустите приложение, развернутое с [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] из веб-браузера, указав URL-адрес манифеста развертывания. При вызове вашей [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения `ClickOnceOnDemand`и передать его в корневом каталоге adatum.com, URL-адрес будет выглядеть следующим образом:  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3.  Когда появится основная форма, нажмите <xref:System.Windows.Forms.Button>. Должна появиться строка в окне сообщений, который считывает «Hello, World!».  
  
## <a name="see-also"></a>См. также  
 <xref:System.Deployment.Application.ApplicationDeployment>
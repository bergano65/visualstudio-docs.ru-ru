---
title: 'Пошаговое руководство: Загрузка сборок по требованию с помощью API развертывания ClickOnce | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: de6698f6e635a151a0f78eecbb90f4d7bd525969
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151279"
---
# <a name="walkthrough-download-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Пошаговое руководство: Загрузка сборок по требованию с помощью API развертывания ClickOnce
По умолчанию все сборки включены в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения загружаются при первом запуске приложения. Тем не менее возможно, частей приложения, которые используются с небольшого набора пользователей. В этом случае рекомендуется скачивать сборку только при создании одного из ее типов. Следующий пример демонстрирует, как пометить определенные сборки в приложении как «необязательные» и как их загрузить с помощью классов в <xref:System.Deployment.Application> пространства имен, если они необходимы для общеязыковой среды выполнения (CLR).  
  
> [!NOTE]
>  Для выполнения данной процедуры приложение должно выполняться с полным доверием.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Требуется один из следующих компонентов для выполнения этого пошагового руководства:  
  
-   Windows SDK. Пакет Windows SDK можно загрузить из центра загрузки Майкрософт.  
  
-   Visual Studio.  
  
## <a name="create-the-projects"></a>Создание проектов  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>Чтобы создать проект, использующий сборку по запросу  
  
1.  Создайте каталог с именем ClickOnceOnDemand.  
  
2.  Откройте окно командной строки Windows SDK или [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] командной строки.  
  
3.  Перейдите в каталог ClickOnceOnDemand.  
  
4.  Создайте пару открытого и закрытого ключей, используя следующую команду:  
  
    ```cmd  
    sn -k TestKey.snk  
    ```  
  
5.  С помощью блокнота или другого текстового редактора, определите класс с именем `DynamicClass` с одним свойством `Message`.  
  
     [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]
     [!code-csharp[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]  
  
6.  Сохраните файл с именем *ClickOnceLibrary.cs* или *ClickOnceLibrary.vb*, в зависимости от используемого языка, к *ClickOnceOnDemand* каталога.  
  
7.  Скомпилируйте файл в сборку.  
  
    ```csharp  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8.  Чтобы получить токен открытого ключа для сборки, используйте следующую команду:  
  
    ```cmd  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. Создайте новый файл, используя текстовый редактор и введите следующий код. Этот код создает приложение Windows Forms, который загружает сборку ClickOnceLibrary при необходимости.  
  
     [!code-csharp[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.cs)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.vb)]  
  
10. В коде, найдите вызов <xref:System.Reflection.Assembly.LoadFile%2A>.  
  
11. Задайте`PublicKeyToken` значение, которое вы получили ранее.  
  
12. Сохраните файл как *Form1.cs* или *Form1.vb*.  
  
13. Скомпилируйте его в исполняемый файл, выполнив следующую команду.  
  
    ```csharp  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## <a name="mark-assemblies-as-optional"></a>Пометьте сборки как необязательные  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>Пометка сборок как необязательных в приложении ClickOnce с помощью MageUI.exe  
  
1.  С помощью *MageUI.exe*, создайте манифест приложения, как описано в [Пошаговое руководство: развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Используйте следующие параметры для манифеста приложения:  
  
    -   Имя манифеста приложения `ClickOnceOnDemand`.  
  
    -   На **файлы** странице *ClickOnceLibrary.dll* строки, задайте **тип файла** столбец **None**.  
  
    -   На **файлы** странице *ClickOnceLibrary.dll* введите `ClickOnceLibrary.dll` в **группы** столбца.  
  
2.  С помощью *MageUI.exe*, создайте манифест развертывания, как описано в разделе [Пошаговое руководство: развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Для манифеста развертывания используйте следующие параметры:  
  
    -   Имя манифеста развертывания `ClickOnceOnDemand`.  
  
## <a name="testing-the-new-assembly"></a>Тестирование новой сборки  
  
#### <a name="to-test-your-on-demand-assembly"></a>Тестирование сборки по запросу  
  
1.  Отправьте ваш [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертывания на веб-сервере.  
  
2.  Запустите приложение, развернутое с помощью [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] из веб-браузера, введя URL-адрес в манифест развертывания. При вызове вашей [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения `ClickOnceOnDemand`и передать его в корневом каталоге adatum.com, URL-адрес будет выглядеть следующим образом:  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3.  Когда появится основная форма, нажмите <xref:System.Windows.Forms.Button>. Вы должны увидеть строку в окне сообщения, который считывает «Hello, World!».  
  
## <a name="see-also"></a>См. также  
 <xref:System.Deployment.Application.ApplicationDeployment>
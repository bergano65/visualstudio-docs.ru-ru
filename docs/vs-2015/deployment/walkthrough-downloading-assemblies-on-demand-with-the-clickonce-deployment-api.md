---
title: Пошаговое руководство. Загрузка сборок по требованию с помощью API развертывания ClickOnce | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 55dfa9a360d33a73b6298f186d12810f8510b1fc
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60063560"
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Пошаговое руководство. Загрузка сборок по требованию с помощью API развертывания ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

По умолчанию все сборки включены в [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения загружаются при первом запуске приложения. Тем не менее возможно, частей приложения, которые используются с небольшого набора пользователей. В этом случае рекомендуется скачивать сборку только при создании одного из ее типов. В следующем примере показано, как пометить определенные сборки в приложении как "необязательные" и скачивать их с помощью классов в пространстве имен <xref:System.Deployment.Application>, когда среда CLR нуждается в них.  
  
> [!NOTE]
>  Для выполнения данной процедуры приложение должно выполняться с полным доверием.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Требуется один из следующих компонентов для выполнения этого пошагового руководства:  
  
- Windows SDK. Пакет Windows SDK можно загрузить из центра загрузки Майкрософт.  
  
- Visual Studio.  
  
## <a name="creating-the-projects"></a>Создание проектов  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>Чтобы создать проект, использующий сборку по запросу  
  
1. Создайте каталог с именем ClickOnceOnDemand.  
  
2. Откройте окно командной строки Windows SDK или [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] командной строки.  
  
3. Перейдите в каталог ClickOnceOnDemand.  
  
4. Создайте пару открытого и закрытого ключей, используя следующую команду:  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5. С помощью блокнота или другого текстового редактора, определите класс с именем `DynamicClass` с одним свойством `Message`.  
  
     [!code-csharp[ClickOnceLibrary#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceLibrary/CS/Class1.cs#1)]
     [!code-vb[ClickOnceLibrary#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceLibrary/VB/Class1.vb#1)]  
  
6. Сохраните файл с именем `ClickOnceLibrary.cs` или `ClickOnceLibrary.vb`в зависимости от используемого языка, каталогу ClickOnceOnDemand.  
  
7. Скомпилируйте файл в сборку.  
  
    ```csharp  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8. Чтобы получить токен открытого ключа для сборки, используйте следующую команду:  
  
    ```  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. Создайте новый файл, используя текстовый редактор и введите следующий код. Этот код создает приложение Windows Forms, который загружает сборку ClickOnceLibrary при необходимости.  
  
     [!code-csharp[ClickOnceOnDemandCmdLine#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/CS/Form1.cs#1)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/VB/Form1.vb#1)]  
  
10. В коде, найдите вызов <xref:System.Reflection.Assembly.LoadFile%2A>.  
  
11. Задайте`PublicKeyToken` значение, которое вы получили ранее.  
  
12. Сохраните файл как `Form1.cs` или `Form1.vb`.  
  
13. Скомпилируйте его в исполняемый файл, выполнив следующую команду.  
  
    ```csharp  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## <a name="marking-assemblies-as-optional"></a>Пометка сборок как необязательных  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>Пометка сборок как необязательных в приложении ClickOnce с помощью MageUI.exe  
  
1. С помощью MageUI.exe, создайте манифест приложения, как описано в разделе [Пошаговое руководство: Развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Используйте следующие параметры для манифеста приложения:  
  
    - Имя манифеста приложения `ClickOnceOnDemand`.  
  
    - На **файлы** , в строке ClickOnceLibrary.dll задать **тип файла** столбец **None**.  
  
    - На **файлы** страницы, в строке ClickOnceLibrary.dll тип `ClickOnceLibrary.dll` в **группы** столбца.  
  
2. С помощью MageUI.exe, создайте манифест развертывания, как описано в разделе [Пошаговое руководство: Развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Для манифеста развертывания используйте следующие параметры:  
  
    - Имя манифеста развертывания `ClickOnceOnDemand`.  
  
## <a name="testing-the-new-assembly"></a>Тестирование новой сборки  
  
#### <a name="to-test-your-on-demand-assembly"></a>Тестирование сборки по запросу  
  
1. Отправьте ваш [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] развертывания на веб-сервере.  
  
2. Запустите приложение, развернутое с помощью [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] из веб-браузера, введя URL-адрес в манифест развертывания. При вызове вашей [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения `ClickOnceOnDemand`и передать его в корневом каталоге adatum.com, URL-адрес будет выглядеть следующим образом:  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3. Когда появится основная форма, нажмите <xref:System.Windows.Forms.Button>. В окне сообщения вы должны видеть строку "Hello, World!".  
  
## <a name="see-also"></a>См. также  
 <xref:System.Deployment.Application.ApplicationDeployment>

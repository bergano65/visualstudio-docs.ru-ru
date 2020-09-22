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
ms.openlocfilehash: af03329a05501427f6d04d6cddbd637c3311b339
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842761"
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Пошаговое руководство. Загрузка сборок по требованию с помощью API развертывания ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

По умолчанию все сборки, включенные в [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложение, загружаются при первом запуске приложения. Однако у вас могут быть части приложения, которые используются небольшим набором пользователей. В этом случае рекомендуется скачивать сборку только при создании одного из ее типов. В следующем примере показано, как пометить определенные сборки в приложении как "необязательные" и скачивать их с помощью классов в пространстве имен <xref:System.Deployment.Application>, когда среда CLR нуждается в них.  
  
> [!NOTE]
> Для выполнения данной процедуры приложение должно выполняться с полным доверием.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этого пошагового руководства потребуется один из следующих компонентов:  
  
- Windows SDK. Windows SDK можно скачать в центре загрузки Майкрософт.  
  
- Visual Studio.  
  
## <a name="creating-the-projects"></a>Создание проектов  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>Создание проекта, использующего сборку по запросу  
  
1. Создайте каталог с именем Кликконцеондеманд.  
  
2. Откройте командную строку Windows SDK или [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] командную строку.  
  
3. Перейдите в каталог Кликконцеондеманд.  
  
4. Создайте пару открытого и закрытого ключей с помощью следующей команды:  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5. С помощью блокнота или другого текстового редактора определите класс `DynamicClass` с именем и одним свойством с именем `Message` .  
  
     [!code-csharp[ClickOnceLibrary#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceLibrary/CS/Class1.cs#1)]
     [!code-vb[ClickOnceLibrary#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceLibrary/VB/Class1.vb#1)]  
  
6. Сохраните текст в файле с именем `ClickOnceLibrary.cs` или в `ClickOnceLibrary.vb` зависимости от используемого языка в каталоге кликконцеондеманд.  
  
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
  
9. Создайте новый файл в текстовом редакторе и введите следующий код. Этот код создает Windows Forms приложение, которое скачивает сборку ClickOnceLibrary, когда это необходимо.  
  
     [!code-csharp[ClickOnceOnDemandCmdLine#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/CS/Form1.cs#1)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/VB/Form1.vb#1)]  
  
10. В коде нахождение вызова <xref:System.Reflection.Assembly.LoadFile%2A> .  
  
11. Задайте `PublicKeyToken` значение, полученное ранее.  
  
12. Сохраните файл как `Form1.cs` или `Form1.vb` .  
  
13. Скомпилируйте его в исполняемый файл с помощью следующей команды.  
  
    ```csharp  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## <a name="marking-assemblies-as-optional"></a>Пометка сборок как необязательных  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>Чтобы пометить сборки как необязательные в приложении ClickOnce с помощью MageUI.exe  
  
1. С помощью MageUI.exe создайте манифест приложения, как описано в разделе [Пошаговое руководство. Развертывание приложения ClickOnce вручную](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Используйте следующие параметры для манифеста приложения:  
  
    - Назовите манифест приложения `ClickOnceOnDemand` .  
  
    - На странице **файлы** в строке ClickOnceLibrary.dll задайте для столбца **Тип файла** значение **нет**.  
  
    - На странице **файлы** в строке ClickOnceLibrary.dll введите `ClickOnceLibrary.dll` в столбец **Группа** .  
  
2. С помощью MageUI.exe создайте манифест развертывания, как описано в разделе [Пошаговое руководство. Развертывание приложения ClickOnce вручную](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Используйте следующие параметры для манифеста развертывания:  
  
    - Присвойте имя манифесту развертывания `ClickOnceOnDemand` .  
  
## <a name="testing-the-new-assembly"></a>Тестирование новой сборки  
  
#### <a name="to-test-your-on-demand-assembly"></a>Тестирование сборки по запросу  
  
1. Загрузите [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] развертывание на веб-сервер.  
  
2. Запустите приложение, развернутое с помощью [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] из веб-браузера, введя URL-адрес манифеста развертывания. Если вы вызываете [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложение `ClickOnceOnDemand` и отправляете его в корневой каталог adatum.com, ваш URL-адрес будет выглядеть следующим образом:  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3. Когда появится основная форма, нажмите <xref:System.Windows.Forms.Button>. В окне сообщения вы должны видеть строку "Hello, World!".  
  
## <a name="see-also"></a>См. также  
 <xref:System.Deployment.Application.ApplicationDeployment>

---
title: Отладка ClickOnce-приложений, использующих System.Deployment.Application | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, debugging
- debugging, ClickOnce applications
- debugging, System.Deployment
- deploying applications [ClickOnce], debugging
ms.assetid: 86f31948-2ca8-47c0-8e8b-c2b817bbf79f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5bf26cfc6f494437b0fde9c3721b11612d4f7e45
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081609"
---
# <a name="debug-clickonce-applications-that-use-systemdeploymentapplication"></a>Отладка ClickOnce-приложений, использующих System.Deployment.Application
В [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертывания можно настроить способ обновления приложения. Тем не менее, если вам нужно использовать и настраивать дополнительные [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] возможности развертывания, необходимо будет получить доступ к объектной модели развертывания, предоставляемые <xref:System.Deployment.Application>. Можно использовать <xref:System.Deployment.Application> API-интерфейсы для сложных задач, таких как:  
  
-   Создание параметра «Обновить сейчас» в приложении  
  
-   Условный, загрузки по требованию различных компонентов приложения  
  
-   Обновления, интегрированные непосредственно в приложение  
  
-   Гарантируя, что клиентское приложение всегда актуальна  
  
 Так как <xref:System.Deployment.Application> API-интерфейсы работают только тогда, когда приложение развертывается с [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] технологии, является единственным способом выполнять их отладку, развертывание приложения с помощью [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], присоединить к ней, а затем выполнить его отладку. Он может быть трудно присоединить отладчик достаточно рано, поскольку этот код часто выполняется, когда приложение запускается и выполняется до подключения отладчика. Решение — поместить прерываний (или остановок, для проектов Visual Basic) перед кодом проверки обновления или код по требованию.  
  
 Рекомендуемый способ отладки выглядит следующим образом:  
  
1.  Перед началом работы убедитесь, что архивируются символов (.pdb) и исходных файлов.  
  
2.  Развертывание первой версии приложения.  
  
3.  Создайте новое пустое решение. Из **файл** меню, щелкните **New**, затем **проекта**. В **новый проект** , открытом окне **другие типы проектов** узел, затем выберите **решения Visual Studio** папки. В **шаблоны** области выберите **пустое решение**.  
  
4.  Добавьте расположение архивированный исходный к свойствам нового решения. В **обозревателе решений**, щелкните правой кнопкой мыши узел решения, а затем нажмите кнопку **свойства**. В **страницы свойств** выберите **исходные файлы отладки**, затем добавьте каталог архивированный исходный код. В противном случае отладчик будет найти устаревшие исходные файлы, так как пути к исходным файлам записываются в PDB-файл. Если отладчик использует устаревшие исходные файлы, вы увидите сообщение о том, что источник не совпадает.  
  
5.  Убедитесь, что отладчик может найти *.pdb* файлов. Если вы развернули их с вашим приложением, отладчик находит их автоматически. Она всегда ищет сборки в вопросе сначала. В противном случае необходимо добавить путь к архиву, чтобы **символов (PDB)** (для доступа к этому параметру, из **средства** меню, щелкните **параметры**, затем откройте  **Отладка** и щелкните **символы**).  
  
6.  Отладка, что происходит между `CheckForUpdate` и `Download` / `Update` вызовы методов.  
  
     Например обновленный код может выглядеть следующим образом:  
  
    ```vb
        Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
            If My.Application.Deployment.IsNetworkDeployed Then  
  
                If (My.Application.Deployment.CheckForUpdate()) Then  
  
                    My.Application.Deployment.Update()  
                    Application.Restart()  
  
                End If  
  
            End If  
        End Sub  
    ```  
  
7.  Развертывание версии 2.  
  
8.  Попытка подключить отладчик к приложению версии 1, так как оно загружает обновление для версии 2. Кроме того, вы можете использовать `System.Diagnostics.Debugger.Break` метода или просто `Stop` в Visual Basic. Само собой эти вызовы методов не следует оставить в рабочем коде.  
  
     Например предположим, вы разрабатываете приложение Windows Forms и имеется обработчик событий для этого метода с логику обновления в ней. Для отладки этого просто прикрепите до нажатия кнопки, затем установите точку останова (Убедитесь, что при открытии соответствующего файла архива и установите точку останова там).  
  
 Используйте <xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A> вызываемому свойству <xref:System.Deployment.Application> API-интерфейсы только в том случае, если приложение развертывается; API-интерфейсы не должны вызываться во время отладки в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>См. также  
 <xref:System.Deployment.Application>
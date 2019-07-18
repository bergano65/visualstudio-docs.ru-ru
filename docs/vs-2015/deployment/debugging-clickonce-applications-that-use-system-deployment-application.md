---
title: Отладка ClickOnce-приложений, использующих System.Deployment.Application | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c0b12faf451d3ed9bb70e2bb1ec6c8503cfb86d5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68187799"
---
# <a name="debugging-clickonce-applications-that-use-systemdeploymentapplication"></a>Отладка ClickOnce-приложений, использующих System.Deployment.Application
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] развертывания можно настроить способ обновления приложения. Тем не менее, если вам нужно использовать и настраивать дополнительные [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] возможности развертывания, необходимо будет получить доступ к объектной модели развертывания, предоставляемые <xref:System.Deployment.Application>. Можно использовать <xref:System.Deployment.Application> API-интерфейсы для сложных задач, таких как:  
  
- Создание параметра «Обновить сейчас» в приложении  
  
- Условный, загрузки по требованию различных компонентов приложения  
  
- Обновления, интегрированные непосредственно в приложение  
  
- Гарантируя, что клиентское приложение всегда актуальна  
  
  Так как <xref:System.Deployment.Application> API-интерфейсы работают только тогда, когда приложение развертывается с [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] технологии, является единственным способом выполнять их отладку, развертывание приложения с помощью [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], присоединить к ней, а затем выполнить его отладку. Он может быть трудно присоединить отладчик достаточно рано, поскольку этот код часто выполняется, когда приложение запускается и выполняется до подключения отладчика. Решение — поместить прерываний (или остановок, для проектов Visual Basic) перед кодом проверки обновления или код по требованию.  
  
  Рекомендуемый способ отладки выглядит следующим образом:  
  
1. Перед началом работы убедитесь, что архивируются символов (.pdb) и исходных файлов.  
  
2. Развертывание первой версии приложения.  
  
3. Создайте новое пустое решение. Из **файл** меню, щелкните **New**, затем **проекта**. В **новый проект** , открытом окне **другие типы проектов** узел, затем выберите **решения Visual Studio** папки. В **шаблоны** области выберите **пустое решение**.  
  
4. Добавьте расположение архивированный исходный к свойствам нового решения. В **обозревателе решений**, щелкните правой кнопкой мыши узел решения, а затем нажмите кнопку **свойства**. В **страницы свойств** выберите **исходные файлы отладки**, затем добавьте каталог архивированный исходный код. В противном случае отладчик будет найти устаревшие исходные файлы, так как пути к исходным файлам записываются в PDB-файл. Если отладчик использует устаревшие исходные файлы, вы увидите сообщение о том, что источник не совпадает.  
  
5. Убедитесь, что отладчик может найти PDB-файлы. Если вы развернули их с вашим приложением, отладчик находит их автоматически. Она всегда ищет сборки в вопросе сначала. В противном случае необходимо добавить путь к архиву, чтобы **символов (PDB)** (для доступа к этому параметру, из **средства** меню, щелкните **параметры**, затем откройте  **Отладка** и щелкните **символы**).  
  
6. Отладка, что происходит между `CheckForUpdate` и `Download` / `Update` вызовы методов.  
  
    Например обновленный код может выглядеть следующим образом:  
  
   ```  
       Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
           If My.Application.Deployment.IsNetworkDeployed Then  
  
               If (My.Application.Deployment.CheckForUpdate()) Then  
  
                   My.Application.Deployment.Update()  
                   Application.Restart()  
  
               End If  
  
           End If  
       End Sub  
   ```  
  
7. Развертывание версии 2.  
  
8. Попытка подключить отладчик к приложению версии 1, так как оно загружает обновление для версии 2. Кроме того, вы можете использовать `System.Diagnostics.Debugger.Break` метода или просто `Stop` в Visual Basic. Само собой эти вызовы методов не следует оставить в рабочем коде.  
  
    Например предположим, вы разрабатываете приложение Windows Forms и имеется обработчик событий для этого метода с логику обновления в ней. Для отладки этого просто прикрепите до нажатия кнопки, затем установите точку останова (Убедитесь, что при открытии соответствующего файла архива и установите точку останова там).  
  
   Используйте <xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A> вызываемому свойству <xref:System.Deployment.Application> API-интерфейсы только в том случае, если приложение развертывается; API-интерфейсы не должны вызываться во время отладки в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>См. также  
 <xref:System.Deployment.Application>

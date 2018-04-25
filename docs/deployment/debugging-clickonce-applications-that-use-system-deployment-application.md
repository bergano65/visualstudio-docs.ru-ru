---
title: Отладка ClickOnce-приложений, использующих System.Deployment.Application | Документы Microsoft
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
ms.openlocfilehash: 30cbf4aab2975b95703c24462604c1a43ed3554c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="debugging-clickonce-applications-that-use-systemdeploymentapplication"></a>Отладка ClickOnce-приложений, использующих System.Deployment.Application
В [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертывания можно настроить способ обновления приложения. Тем не менее, если вам нужно использовать и настроить дополнительные [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] возможности развертывания, необходимо будет получить доступ к объектной модели развертывания, предоставляемой объектом <xref:System.Deployment.Application>. Можно использовать <xref:System.Deployment.Application> API-интерфейсы для сложных задач, таких как:  
  
-   Создание параметра «Обновить сейчас» в приложении  
  
-   Условные загрузки по требованию различных компонентов приложения  
  
-   Обновления интегрируется непосредственно в приложение  
  
-   Что гарантирует, что клиентское приложение всегда актуален  
  
 Поскольку <xref:System.Deployment.Application> API-интерфейсы работают только тогда, когда приложение развертывается с [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] технологии, единственным способом их отладки является развертывание приложения с помощью [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], присоединиться к нему, а затем его отладку. Он может быть трудно присоединить отладчик достаточно рано, поскольку этот код часто выполняется, когда приложение запускается и выполняет, прежде чем можно будет присоединить отладчик. Решением этой проблемы является размещение прерываний (или остановок для проектов Visual Basic) перед кодом проверки обновления или кодом по требованию.  
  
 Рекомендуемым способом отладки выглядит следующим образом:  
  
1.  Прежде чем начать, убедитесь, что архивируются символов (.pdb) и исходных файлов.  
  
2.  Развертывание версии 1 приложения.  
  
3.  Создайте новое пустое решение. Из **файл** меню, нажмите кнопку **New**, затем **проекта**. В **новый проект** открытия диалогового окна, **другие типы проектов** узел, затем выберите **решения Visual Studio** папки. В **шаблоны** выберите **пустое решение**.  
  
4.  Добавьте местоположение архивированного исходного свойства нового решения. В **обозревателе решений**, щелкните правой кнопкой мыши узел решения, а затем нажмите кнопку **свойства**. В **страницы свойств** выберите **исходные файлы отладки**, затем добавьте каталог архивированного исходного кода. В противном случае отладчик найдет устаревшие исходные файлы, поскольку пути к исходным файлам записываются в PDB-файл. Если отладчик использует устаревшие исходные файлы, может появиться сообщение о том, что источник не совпадает.  
  
5.  Убедитесь, что отладчик может найти PDB-файлы. Если вы развернули их с приложением, отладчик находит их автоматически. Он всегда выполняет поиск сборки в вопросе сначала. В противном случае необходимо добавить путь к архиву для **символов (PDB)** (для доступа к этому параметру, из **средства** меню, нажмите кнопку **параметры**, затем откройте  **Отладка** и щелкните **символы**).  
  
6.  Отладка, что происходит между `CheckForUpdate` и `Download` / `Update` вызовы методов.  
  
     Например обновите код может выглядеть следующим образом:  
  
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
  
7.  Разверните версию 2.  
  
8.  Попытка присоединить отладчик к приложению версии 1, когда оно загружает обновление для версии 2. Можно также использовать `System.Diagnostics.Debugger.Break` метода или просто `Stop` в Visual Basic. Конечно нельзя оставлять эти вызовы методов в рабочем коде.  
  
     Например предположим, вы разрабатываете приложение Windows Forms, и имеется обработчик событий для этого метода с логику обновления в ней. Чтобы отладить это, просто присоединить до нажатия кнопки, то установите точку останова (убедитесь в том, откройте нужный архивный файл и задать точку останова в ней).  
  
 Используйте <xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A> свойство для вызова <xref:System.Deployment.Application> API-интерфейсы только в том случае, если приложение развертывается; API-интерфейсы не должны вызываться во время отладки в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>См. также  
 <xref:System.Deployment.Application>
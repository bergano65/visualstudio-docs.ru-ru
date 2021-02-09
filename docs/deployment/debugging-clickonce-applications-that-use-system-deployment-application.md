---
title: Отладка приложений ClickOnce, использующих System. Deployment. Application
description: Узнайте, как использовать и настраивать дополнительные функции развертывания ClickOnce путем доступа к объектной модели развертывания, предоставляемой System. Deployment. Application.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d6a014afff6c26b8cfe8f4f7fae508f78ef5905f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912241"
---
# <a name="debug-clickonce-applications-that-use-systemdeploymentapplication"></a>Отладка приложений ClickOnce, использующих System.Deployment.Application
В [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертывание позволяет настраивать способ обновления приложения. Однако если необходимо использовать и настроить дополнительные [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] функции развертывания, необходимо получить доступ к объектной модели развертывания, предоставляемой <xref:System.Deployment.Application> . Интерфейсы API можно использовать <xref:System.Deployment.Application> для расширенных задач, таких как:

- Создание параметра "Обновить сейчас" в приложении

- Условная загрузка по запросу различных компонентов приложения

- Обновления, интегрированные непосредственно в приложение

- Гарантия того, что клиентское приложение всегда находится в актуальном состоянии

  Поскольку <xref:System.Deployment.Application> API-интерфейсы работают только при развертывании приложения с помощью [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] технологии, единственным способом его отладки является развертывание приложения с помощью [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , присоединение к нему, а затем Отладка. Присоединение отладчика может быть затруднительным, так как этот код часто запускается, когда приложение запускается и исполняется, прежде чем можно будет присоединить отладчик. Решение заключается в помещении перерывов (или прекращений для Visual Basic проектов) перед кодом проверки обновлений или кодом по требованию.

  Рекомендуется использовать следующий метод отладки:

1. Прежде чем начать, убедитесь, что символы (. pdb) и исходные файлы архивируются.

2. Развертывание версии 1 приложения.

3. Создайте новое пустое решение. В меню **Файл** выберите **Создать**,а затем — **Проект**. В диалоговом окне **Новый проект** откройте узел **другие типы проектов** , а затем выберите папку **решения Visual Studio** . В области **шаблоны** выберите **пустое решение**.

4. Добавьте заархивированное исходное расположение в свойства этого нового решения. В **Обозреватель решений** щелкните правой кнопкой мыши узел решения и выберите пункт **свойства**. В диалоговом окне **страницы свойств** выберите **исходные файлы отладки**, а затем добавьте каталог архивированного исходного кода. В противном случае отладчик найдет актуальные исходные файлы, так как пути к исходным файлам записываются в PDB-файл. Если отладчик использует неактуальные исходные файлы, появится сообщение о том, что источник не соответствует.

5. Убедитесь, что отладчик может найти *pdb* -файлы. Если вы развернули их вместе с приложением, отладчик найдет их автоматически. Сначала он всегда выглядит рядом с самой сборкой. В противном случае необходимо будет добавить путь к архиву в **расположения файлов символов (. pdb)** (для доступа к этому параметру в меню **Сервис** выберите **Параметры**, затем откройте узел **Отладка** и щелкните **символы**).

6. Отладка того, что происходит между `CheckForUpdate` `Download` / `Update` вызовами метода и.

    Например, код обновления может выглядеть следующим образом:

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

7. Развертывание версии 2.

8. Попытка подключить отладчик к приложению версии 1 по мере загрузки обновления для версии 2. Кроме того, можно использовать `System.Diagnostics.Debugger.Break` метод или просто `Stop` в Visual Basic. Конечно, не следует оставлять эти вызовы методов в рабочем коде.

    Например, предположим, что вы разрабатываете приложение Windows Forms и у вас есть обработчик событий для этого метода с логикой обновления. Чтобы выполнить отладку, просто присоединитесь перед нажатием кнопки, а затем установите точку останова (убедитесь, что вы откроете соответствующий архивный файл и установите в нем точку останова).

   Используйте <xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A> свойство для вызова <xref:System.Deployment.Application> API только при развертывании приложения. API не следует вызывать во время отладки в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>См. также раздел
- <xref:System.Deployment.Application>
---
title: Как задать версию публикации ClickOnce | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, setting publish version
- publishing, ClickOnce
- Publish Version property
ms.assetid: 06f15504-6385-40a6-b01d-cd90ca36dc73
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ec5d5d742b5a0749d1d5d52cee0a0545dd8570f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842672"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Практическое руководство. Установка версии публикации приложения ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] `Publish Version` Свойство определяет, будет ли публикуемое приложение рассматриваться как обновление. Каждый раз, когда версия увеличивается, приложение будет опубликовано как обновление.  
  
 Это `Publish Version` свойство можно задать на странице **Публикация** **конструктора проектов**.  
  
> [!NOTE]
> Существует параметр проекта, который будет автоматически увеличивать свойство при `Publish Version` каждом публикации приложения. Этот параметр включен по умолчанию. Дополнительные сведения см. в разделе [инструкции. автоматическое увеличение версии публикации ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).  
  
### <a name="to-change-the-publish-version"></a>Изменение версии публикации  
  
1. Выбрав проект в **Обозреватель решений**, в меню **проект** выберите пункт **Свойства**.  
  
2. Перейдите на вкладку **Публикация**.  
  
3. В поле **Версия публикации** Увеличьте номер версии **основного**, **дополнительного**, Номера **сборки**или **редакции** .  
  
    > [!NOTE]
    > Не следует уменьшать номер версии. Это может привести к непредсказуемому поведению обновления.  
  
## <a name="see-also"></a>См. также:  
 [Выбор стратегии обновления ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Как автоматически увеличивать версию публикации ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Практическое руководство. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)

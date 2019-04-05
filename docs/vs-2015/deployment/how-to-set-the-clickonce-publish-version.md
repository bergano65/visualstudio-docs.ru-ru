---
title: Практическое руководство. Установка ClickOnce версии публикации | Документация Майкрософт
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
ms.openlocfilehash: b082e92ffac43e48725285bc9fa9052dd82cfd92
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58992169"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Практическое руководство. Установка версии публикации приложения ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] `Publish Version` Свойство определяет ли приложение, которое вы публикуете будет рассматриваться как обновление. Каждая версия времени увеличивается, приложение будет опубликовано как обновление.  
  
 `Publish Version` Может быть установлено на **публикации** странице **конструктор проектов**.  
  
> [!NOTE]
>  Имеется параметр проекта, который автоматически увеличивает `Publish Version` свойство каждый раз при публикации приложения; этот параметр включен по умолчанию. Дополнительные сведения см. в разделе [Как автоматически увеличить номера версии публикации ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).  
  
### <a name="to-change-the-publish-version"></a>Изменение версии публикации  
  
1.  Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2.  Перейдите на вкладку **Публикация**.  
  
3.  В **версия публикации** поле, приращение **основных**, **незначительные**, **построения**, или **редакции** версии номера.  
  
    > [!NOTE]
    >  Вы никогда не следует уменьшения номером версии; Это может привести к непредсказуемым обновления поведение.  
  
## <a name="see-also"></a>См. также  
 [Выбор стратегии обновления ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Практическое руководство. Автоматически ClickOnce увеличение номера версии публикации](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Практическое руководство. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)

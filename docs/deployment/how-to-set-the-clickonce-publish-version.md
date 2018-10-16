---
title: 'Практическое: Установка ClickOnce версии публикации | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c991975a369387fea248816f4465670f1062a927
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080230"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Практическое: Установка ClickOnce версии публикации
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version` Свойство определяет ли приложение, которое вы публикуете будет рассматриваться как обновление. Каждая версия времени увеличивается, приложение будет опубликовано как обновление.  
  
 `Publish Version` Может быть установлено на **публикации** странице **конструктор проектов**.  
  
> [!NOTE]
>  Имеется параметр проекта, который автоматически увеличивает `Publish Version` свойство каждый раз при публикации приложения; этот параметр включен по умолчанию. Дополнительные сведения см. в разделе [как: автоматическое увеличение версии публикации ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).  
  
### <a name="to-change-the-publish-version"></a>Изменение версии публикации  
  
1.  Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2.  Нажмите кнопку **публикации** вкладки.  
  
3.  В **версия публикации** поле, приращение **основных**, **незначительные**, **построения**, или **редакции** версии номера.  
  
    > [!NOTE]
    >  Вы никогда не следует уменьшения номером версии; Это может привести к непредсказуемым обновления поведение.  
  
## <a name="see-also"></a>См. также  
 [Выбор стратегии обновления ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Практическое: автоматически ClickOnce увеличение номера версии публикации](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Практическое: публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
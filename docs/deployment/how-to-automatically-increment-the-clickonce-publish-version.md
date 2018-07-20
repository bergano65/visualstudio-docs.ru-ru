---
title: 'Практическое: автоматически ClickOnce увеличение номера версии публикации | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], incrementing publish version automatically
- Publish Version property, incrementing
- ClickOnce deployment, incrementing publish version automatically
- publishing, ClickOnce
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: beada30e45ce2d46500654bca5051bd51db02d66
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151968"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Практическое: автоматически ClickOnce увеличение номера версии публикации
При публикации [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения, изменив `Publish Version` свойство заставляет приложение публикуется как обновление. По умолчанию Visual Studio автоматически увеличивает `Revision` число `Publish Version` при каждой публикации приложения.  
  
 Это поведение можно отключить на **публикации** странице **конструктор проектов**.  
  
> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-disable-automatically-incrementing-the-publish-version"></a>Автоматическое отключение увеличения номера версии публикации  
  
1.  Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2.  Нажмите кнопку **публикации** вкладки.  
  
3.  В **версия публикации** снимите **автоматически увеличивать номер редакции при каждой редакции** "флажок".  
  
## <a name="see-also"></a>См. также  
 [Практическое: Установка ClickOnce версии публикации](../deployment/how-to-set-the-clickonce-publish-version.md)   
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Практическое: публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
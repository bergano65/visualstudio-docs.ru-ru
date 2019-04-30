---
title: Практическое руководство. Изменение языка публикации для приложения ClickOnce | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish language property
- ClickOnce deployment, changing publish language
- publishing, ClickOnce
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2a50beda49895396bf9fec48213836a109d8a873
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442184"
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>Практическое руководство. Изменение языка публикации для приложения ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При публикации [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения, пользовательский интерфейс во время установки значения по умолчанию для языка и региональных параметров компьютера разработки. Если вы публикуете локализованного приложения, необходимо будет указать язык и региональные параметры, соответствующие локализованной версии. Это определяется параметром `Publish language` свойство проекта.  
  
 `Publish language` Может быть установлено **параметры публикации** окне доступен из **публикации** странице **конструктор проектов**.  
  
> [!NOTE]
> Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-change-the-publish-language"></a>Чтобы изменить язык публикации  
  
1. Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2. Перейдите на вкладку **Публикация**.  
  
3. Нажмите кнопку **параметры** кнопку, чтобы открыть **параметры публикации** диалоговое окно.  
  
4. Нажмите кнопку **описание**.  
  
5. В **параметры публикации** диалоговое окно, выберите язык и язык и региональные параметры из **язык публикации** стрелку раскрывающегося списка и нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Практическое руководство. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)

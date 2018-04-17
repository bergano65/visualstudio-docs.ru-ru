---
title: 'Как: изменение языка публикации для приложения ClickOnce | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
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
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: f6b1590eb45950cb0e8b9de668b7eabe62d13c3b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>Практическое руководство. Изменение языка публикации для приложения ClickOnce
При публикации [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения, пользовательский интерфейс, отображаемый во время установки значения по умолчанию для языка и региональных параметров компьютера разработки. При публикации локализованного приложения необходимо указать язык и региональные параметры, соответствующие локализованной версии. Это определяется `Publish language` свойство проекта.  
  
 `Publish language` Может быть установлено **параметры публикации** окне доступен из **публикации** страница **конструктора проектов**.  
  
> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-change-the-publish-language"></a>Изменение языка публикации  
  
1.  Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2.  Нажмите кнопку **публикации** вкладки.  
  
3.  Нажмите кнопку **параметры** кнопку, чтобы открыть **параметры публикации** диалоговое окно.  
  
4.  Нажмите кнопку **описание**.  
  
5.  В **параметры публикации** диалоговое окно, выберите язык и язык и региональные параметры из **язык публикации** раскрывающегося списка и нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Практическое руководство. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
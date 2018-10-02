---
title: 'Практическое: задание имени в меню Пуск для ClickOnce-приложения | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 303d2cb53ce65fdc4a53a039c78664316579fece
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558410"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>Практическое руководство. Задание имени в меню "Пуск" для приложения ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: укажите имя меню Пуск для приложения ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application).  
  
Когда [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] установлено приложение для использования сетевой и автономный режим, чтобы добавляется запись **запустить** меню и **Установка и удаление программ** списка. По умолчанию, отображаемое имя совпадает с именем сборки приложения, но отображаемое имя можно изменить, задав **название продукта** в **параметры публикации** диалоговое окно.  
  
 **Название продукта** будет отображаться на странице publish.htm; для установленного автономного приложения, он будет использоваться имя элемента в **запустить** меню, а также будет имя, которое отображается в **добавления или удаления Программы**.  
  
 **Имя издателя** будет отображаться на странице publish.htm выше **название продукта**, и для установленного автономного приложения, он также будет имя папки, который содержит значок приложения в **запуск**  меню.  
  
 Можно задать **название продукта** и **имя издателя** свойств в **параметры публикации** диалоговом окне на **публикации** страницы из **в конструкторе проектов**.  
  
### <a name="to-specify-a-start-menu-name"></a>Для указания имени меню "Пуск"  
  
1.  Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2.  Нажмите кнопку **публикации** вкладки.  
  
3.  Нажмите кнопку **параметры** кнопку, чтобы открыть **параметры публикации** диалоговое окно.  
  
4.  Нажмите кнопку **описание**.  
  
5.  В **параметры публикации** диалогового окна введите имя, отображаемое в **название продукта**.  
  
6.  При необходимости можно ввести имя издателя в **имя издателя**.  
  
## <a name="see-also"></a>См. также  
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Практическое руководство. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)




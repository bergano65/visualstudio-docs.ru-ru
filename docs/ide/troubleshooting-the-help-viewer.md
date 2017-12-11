---
redirect_url: /visualstudio/ide/microsoft-help-viewer
ms.openlocfilehash: c0b1a114eb157860dd70873929727cc56f1d6514
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2017
---
title: "Устранение неполадок окна справки | Документы Майкрософт" ms.custom: "" ms.date: "11.04.2016" ms.reviewer: "" ms.suite: "" ms.technology: 
  - "vs-help-viewer" ms.tgt_pltfrm: "" ms.topic: "article" helpviewer_keywords: 
  - "устранение неполадок [окно справки]"
  - "Окно справки, устранение неполадок" ms.assetid: 461a4553-064a-4142-a2d2-058658b9ba12 caps.latest.revision: 13 author: "gewarren" ms.author: "gewarren" manager: ghogen
---
# <a name="troubleshooting-the-help-viewer"></a>Устранение неполадок средства просмотра справки
В этом разделе рассматриваются проблемы, с которыми можно столкнуться при работе с окном справки.  
  
## <a name="audio-doesnt-work"></a>Звук не работает.  
 В окне справки нет аудиоплеера. Если вы скачиваете содержимое, содержащее звук, но при выборе элемента **Воспроизвести** ничего не происходит, установите аудиоплеер.  
  
## <a name="search-doesnt-work-in-windows-server-2008-windows-server-2008-with-sp1-or-windows-server-2008-r2"></a>Поиск не работает в Windows Server 2008, Windows Server 2008 с пакетом обновления 1 (SP1) или Windows Server 2008 R2.  
 Для функций поиска и фильтрации в окне справки требуется, чтобы была установлена и включена служба Windows Search. По умолчанию эта служба отключена в Windows Server 2008, Windows Server 2008 с пакетом обновления 1 (SP1) и Windows Server 2008 R2.  
  
#### <a name="to-activate-windows-search-service"></a>Включение службы Windows Search  
  
1.  Запустите диспетчер сервера.  
  
2.  В левой области навигации выберите **Роли**.  
  
3.  В области "Сводка по ролям" выберите **Добавить роль**.  
  
4.  Выберите роль файловых служб, а затем нажмите кнопку **Далее**.  
  
5.  Выберите службу роли Windows Search.  
  
## <a name="additional-resources"></a>Дополнительные ресурсы  
 Вы можете получить дополнительные сведения и предоставить отзыв об окне справки с помощью следующих ресурсов:  
  
-   Чтобы предоставить отзыв, воспользуйтесь страницей [Microsoft Connect](http://go.microsoft.com/fwlink/?linkid=243983) на веб-сайте Майкрософт или отправьте сообщение электронной почты на адрес [hlpfdbk@microsoft.com](mailto:hlpfdbk@microsoft.com).  
  
-   Дополнительные сведения см. на форуме [Документация разработчика и справочная система](http://go.microsoft.com/fwlink/?LinkId=232741).  
  
## <a name="see-also"></a>См. также
[Руководство администратора Help Viewer](http://go.microsoft.com/fwlink/?LinkId=243985)
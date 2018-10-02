---
title: Устранение неполадок средства просмотра справки | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- troubleshooting [Help Viewer 2.0]
- Help Viewer 2.0, troubleshooting
ms.assetid: 461a4553-064a-4142-a2d2-058658b9ba12
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 68946af27925347cee497c237de396d31f214e13
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571266"
---
# <a name="troubleshooting-the-help-viewer"></a>Устранение неполадок средства просмотра справки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Устранение неполадок средства просмотра справки](https://docs.microsoft.com/visualstudio/ide/troubleshooting-the-help-viewer).  
  
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
  
-   Дополнительные сведения см. в разделе [Документация разработчика и справочная система](http://go.microsoft.com/fwlink/?LinkId=232741) форум и [помощник](http://go.microsoft.com/fwlink/?LinkId=232743) блога.  
  
## <a name="see-also"></a>См. также  
 [Руководство администратора Help Viewer 2.1](http://go.microsoft.com/fwlink/?LinkId=243985)




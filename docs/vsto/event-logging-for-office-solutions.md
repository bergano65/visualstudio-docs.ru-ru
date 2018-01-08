---
title: "Ведение журнала событий для решений Office | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], event viewer
- ClickOnce deployment [Office development in Visual Studio], event viewer
- deploying applications [Office development in Visual Studio], event viewer
- Office development in Visual Studio, event viewer
ms.assetid: 31a246fe-ce1c-4f0e-9a21-9cf974c247fe
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 55864eda9d62be5988d1d3ab7262c4d34c0662f9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="event-logging-for-office-solutions"></a>Ведение журнала событий для решений Office
  Вы можете использовать средство просмотра событий в Windows для просмотра сообщений об исключениях, записанных средой выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] при установке или удалении решений Office. С помощью этих сообщений из журнала событий можно разрешать проблемы развертывания и установки.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="reading-the-event-log"></a>Чтение журнала событий  
 Откройте **средство просмотра событий** и отфильтруйте события, которые нужно просмотреть.  
  
#### <a name="to-read-the-event-log-in-windows-server-2003-and-windows-xp"></a>Чтение журнала событий в Windows Server 2003 и Windows XP  
  
1.  В панели управления откройте раздел **Администрирование**.  
  
2.  Запустите **средство просмотра событий**.  
  
3.  В списке журналов событий выберите **Приложение**.  
  
4.  В меню **Представление** выберите пункт **Фильтр**.  
  
5.  В списке **Источник события** выберите **VSTO 4.0**.  
  
6.  Для событий установки в поле **Идентификатор события** введите **4096**.  
  
7.  Нажмите кнопку **ОК** , чтобы просмотреть отфильтрованное представление.  
  
#### <a name="to-read-the-event-log-in-windows-7-windows-vista-and-windows-server-2008"></a>Чтение журнала событий в Windows 7, Windows Vista и Windows Server 2008  
  
1.  В панели управления откройте раздел **Администрирование**.  
  
2.  Запустите **средство просмотра событий**.  
  
3.  Разверните **Журналы Windows**.  
  
4.  В списке журналов событий выберите **Приложение**.  
  
5.  В меню **Действие** меню щелкните **Фильтровать текущий журнал**.  
  
6.  В списке **Источник события** выберите **VSTO 4.0**.  
  
7.  Для событий установки в поле **Идентификатор события** введите **4096**.  
  
8.  Нажмите кнопку **ОК** , чтобы просмотреть отфильтрованное представление.  
  
 Просмотр событий содержит следующие сведения.  
  
-   Расположение манифеста развертывания для решения.  
  
-   Сообщение, описывающее причину ошибки или исключения.  
  
 Эти сообщения об исключениях помогают определить причину проблемы, возникшей при установке, такую как ненадежный сертификат, ненадежное расположение документа или недопустимый манифест развертывания.  
  
 После удаления решения Office сообщения об исключениях остаются в журнале событий.  
  
 Показывать или записывать сообщения об исключениях при запуске решения Office, в разделе [отладка проектов Office](../vsto/debugging-office-projects.md) и [отладка проектов Office](../vsto/debugging-office-projects.md).  
  
### <a name="localization"></a>Локализация  
 Язык сообщений об исключениях определяется языком среды выполнения Visual Studio Tools для Office. Например, если на компьютере пользователя установлен японский языковой пакет, сообщение об исключении записывается в журнал событий на японском языке.  
  
## <a name="disabling-the-event-logger"></a>Отключение журнала событий  
 По умолчанию журнал событий включен при установке или удалении решений Office. Вы можете отключить журнал событий, установив в переменной среды VSTO_EVENTLOGDISABLED значение "1" (один).  
  
#### <a name="to-disable-the-event-log"></a>Отключение журнала событий  
  
1.  В панели управления откройте раздел **Система**.  
  
2.  На вкладке **Дополнительно** нажмите кнопку **Переменные среды**.  
  
3.  В области **Системные переменные** щелкните **Создать**.  
  
4.  В диалоговом окне **создания системной переменной** введите **VSTO_EVENTLOGDISABLED** в поле **Имя переменной** .  
  
5.  В поле **Значение переменной** введите **1**.  
  
6.  Нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Развертывание решения Office](../vsto/deploying-an-office-solution.md)   
 [Устранение неполадок, связанных с развертыванием решения Office](../vsto/troubleshooting-office-solution-deployment.md)  
  
  
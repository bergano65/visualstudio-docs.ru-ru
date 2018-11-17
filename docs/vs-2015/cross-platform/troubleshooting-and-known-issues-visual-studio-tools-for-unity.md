---
title: Устранение неполадок и известные проблемы (инструменты Visual Studio для Unity) | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
caps.latest.revision: 7
author: conceptdev
ms.author: crdun
manager: ghogen
ms.openlocfilehash: 94240d5af43944b23890a32b757fe1b4f14b77ec
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755521"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Устранение неполадок и известные проблемы (набор средств Visual Studio для Unity)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
В этом разделе рассмотрены решения по устранению проблем, типичных для набора средств Visual Studio для Unity, приведено описание известных проблем и показано, как улучшить функционирование набора средств Visual Studio для Unity с помощью отчетов об ошибках.  
  
## <a name="troubleshooting"></a>Устранение неполадок  
 Сведения об устранении некоторых типичных проблем, характерных для набора средств Visual Studio для Unity, см. в следующих разделах.  
  
### <a name="migrating-from-unityvs-to-visual-studio-tools-for-unity"></a>Миграция из UnityVS в набор средств Visual Studio для Unity  
 В случае миграции из UnityVS в набор средств Visual Studio для Unity необходимо создать новые решения Visual Studio для ваших проектов Unity.  
  
##### <a name="to-migrate-your-unity-project-from-unityvs-18-to-visual-studio-tools-for-unity-19"></a>Перенос проекта Unity из UnityVS 1.8 в набор средств Visual Studio для Unity 1.9  
  
1.  Удалите старые файлы решения и проекта из проекта Unity. В корневом каталоге проекта Unity найдите файлы SLN и PROJ (специфические для Visual Studio) и удалите их все.  
  
2.  Импортируйте пакет набора средств Visual Studio для Unity в свой пакет Unity. Дополнительные сведения о том, как импортировать пакет VSTU, см. в разделе "Настройка набора средств Visual Studio для Unity" на странице [Начало работы](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) .  
  
3.  Создайте новые файлы решения и проекта. Если их нужно создать сейчас, в редакторе Unity в главном меню выберите **Средства Visual Studio**, **Создать файлы проекта**. В противном случае этот шаг можно пропустить. Набор средств Visual Studio для Unity автоматически создаст новые файлы при выборе **Средства Visual Studio**, **Открыть в Visual Studio**.  
  
### <a name="visual-studio-wont-load-the-solution-that-visual-studio-tools-for-unity-created"></a>Visual Studio не будет загружать решение, созданное набором средств Visual Studio для Unity.  
 Дополнительные сведения см. в [ответе на этот вопрос на Stackoverflow](http://stackoverflow.com/a/24035907/36702).  
  
### <a name="on-windows-8-visual-studio-asks-to-download-the-unity-target-framework"></a>В ОС Windows 8 система Visual Studio предлагает загрузить целевую платформу Unity  
 Для UnityVS требуется платформа .NET Framework 3.5, которая не установлена по умолчанию в Windows 8. Чтобы устранить эту проблему, следуйте инструкциям по загрузке и установке .NET Framework 3.5.  
  
## <a name="known-issues"></a>Известные проблемы  
 Применительно к набору средств Visual Studio для Unity существуют известные проблемы, которые возникают вследствие взаимодействия отладчика со старой версией компилятора C# в Unity. Мы работаем над устранением этих проблем, но в то же время могут возникать другие проблемы.  
  
-   При отладке Unity иногда аварийно завершает работу.  
  
-   При отладке Unity иногда зависает.  
  
-   Пошаговая отладка с заходом и выходом из методов иногда ведет себя некорректно, особенно в итераторах или внутри инструкций switch.  
  
## <a name="reporting-errors"></a>Ведение отчетов об ошибках  
 Помогите нам улучшить качество набора средств Visual Studio для Unity: отправляйте нам отчеты об ошибках при аварийном выходе, зависании или в случае других ошибок. Эти сведения помогают нам определять причину и устранять проблемы в наборе средств Visual Studio для Unity. Спасибо!  
  
### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Как сообщить об ошибке в случае зависания Visual Studio  
 Существуют отчеты о том, что иногда Visual Studio  зависает при отладке с помощью набора средств Visual Studio для Unity, но чтобы разобраться в проблеме, нам требуется больше данных. Вы можете помочь нам разобраться с проблемой, если выполните следующие действия.  
  
##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Создание отчета о зависании Visual Studio во время отладки с помощью набора средств Visual Studio для Unity  
  
1. Откройте новый экземпляр Visual Studio.  
  
2. Откройте диалоговое окно "Присоединение к процессу". В новом экземпляре Visual Studio в главном меню выберите **Отладка**, **Присоединение к процессу**.  
  
3. Присоедините отладчик к замороженному экземпляру Visual Studio. В диалоговом окне **Присоединение к процессу** выберите замороженный экземпляр Visual Studio в таблице **Доступные процессы** , а затем нажмите кнопку **Присоединить** .  
  
4. Приостановите отладчик. В новом экземпляре Visual Studio в главном меню выберите **Отладка**, **Прервать все** или просто нажмите **CTRL+ALT+BREAK**.  
  
5. Создайте дамп потока. В окне командной строки введите следующую команду и нажмите клавишу **Ввод**.  
  
   ```powershell  
   Debug.ListCallStack /AllThreads /ShowExternalCode  
   ```  
  
    Возможно, сначала будет нужно отобразить окно **Команда** . В Visual Studio в главном меню выберите **Представление**, **Другие окна**, **Командное окно**.  
  
6. Наконец, отправьте дамп потока по адресу [vstusp@microsoft.com](mailto:vstusp@microsoft.com), а также опишите, что вы делали, когда среда Visual Studio зависла.


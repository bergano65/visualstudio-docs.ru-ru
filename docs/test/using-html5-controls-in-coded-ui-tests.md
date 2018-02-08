---
title: "Использование элементов управления HTML5 в закодированных тестах пользовательского интерфейса | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 093457cf2aea3951db89e6fa677ec03fe55df89a
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>Использование элементов управления HTML5 в закодированных тестах пользовательского интерфейса
Закодированные тесты ИП поддерживают некоторые элементы управления HTML5 в Internet Explorer 9 и Internet Explorer 10.  
  
 **Требования**  
  
-   Visual Studio Enterprise  
  
> [!WARNING]
>  В версиях до Internet Explorer 10 можно было выполнять закодированные тесты пользовательского интерфейса на более высоком уровне привилегий, чем у процесса Internet Explorer. Во время выполнения закодированных тестов пользовательского интерфейса на Internet Explorer 10 эти тесты и процесс Internet Explorer должны быть на одинаковом уровне привилегий. Это вызвано более безопасными функции AppContainer в Internet Explorer 10.  
  
> [!WARNING]
>  Если закодированный тест пользовательского интерфейса создан в Internet Explorer 10, он может не работать в Internet Explorer 9 или Internet Explorer 8. Это происходит потому, что Internet Explorer 10 включает элементы управления HTML5, такие как Audio, Video, ProgressBar и Slider. Эти элементы управления HTML5 не распознаются в Internet Explorer 9 или Internet Explorer 8. Таким же образом, закодированный тест пользовательского интерфейса, созданный с помощью Internet Explorer 9, может включать некоторые элементы управления HTML5, которые не распознаются в Internet Explorer 8.  
  
## <a name="supported-html5-controls"></a>Поддерживаемые элементы управления HTML5  
 Закодированный тест пользовательского интерфейса предоставляют поддержку для записи, воспроизведения и проверки следующих элементов управления HTML5:  
  
-   [Элемент управления звуком](#UsingHTML5ControlsCodedUITestsAudio)  
  
-   [Элемент управления видео](#UsingHTML5ControlsCodedUITestsVideo)  
  
-   [Slider](#UsingHTML5ControlsCodedUITestsSlider)  
  
-   [ProgressBar](#UsingHTML5ControlsCodedUITestsProgressBar)  
  
###  <a name="UsingHTML5ControlsCodedUITestsAudio"></a> Элемент управления звуком  
 Действия **элемента управления звуком** на элементе управления звуком HTML5 правильно записываются и воспроизводятся.  
  
 ![Элемент управления звуком HTML5](../test/media/codedui_html5_audio.png "CodedUI_HTML5_Audio")  
  
|Действие|Запись|Созданный код|  
|------------|---------------|--------------------|  
|**Воспроизведение звука**<br /><br /> Непосредственно из элемента управления или в контекстном меню элемента управления.|Воспроизведение аудио \<название> от 00:00:00|HtmlAudio.Play(TimeSpan)|  
|**Переход к определенному моменту времени в аудио**|Переход в аудио \<название> к 00:01:48|HtmlAudio.Seek(TimeSpan)|  
|**Приостановка аудио**<br /><br /> Непосредственно из элемента управления или в контекстном меню элемента управления.|Приостановка аудио \<название> на 00:01:53|HtmlAudio.Pause(TimeSpan)|  
|**Отключение звука**<br /><br /> Непосредственно из элемента управления или в контекстном меню элемента управления.|Отключение звука аудио \<название>|HtmlAudio.Mute()|  
|**Включение звука**<br /><br /> Непосредственно из элемента управления или в контекстном меню элемента управления.|Включение звука аудио \<название>|HtmlAudio.Unmute()|  
|**Изменение громкости звука**|Установка громкости аудио \<название> на 79 %|HtmlAudio.SetVolume(float)|  
  
 Следующие свойства доступны для HtmlAudio и вы можете добавить на них утверждение:  
  
```  
string AutoPlay  
string Controls  
string CurrentSrc  
string CurrentTime  
string CurrentTimeAsString  
string Duration  
string DurationAsString  
string Ended  
string Loop  
string Muted  
string Paused  
string PlaybackRate  
string ReadyState  
string Seeking  
string Src  
string Volume  
  
```  
  
 **Свойства поиска:** Свойства поиска для `HtmlAudio` равны `Id`, `Name` и `Title`.  
  
 **Свойства фильтра:** Свойства фильтра для `HtmlAudio` равны `Src`, `Class`, `ControlDefinition` и `TagInstance`.  
  
> [!NOTE]
>  Период времени для перехода и приостановки может быть значительным. Во время воспроизведения закодированный тест пользовательского интерфейса ожидает время, указанное в `(TimeSpan)` перед приостановкой аудио. Если при каких-то особых обстоятельствах указанное время истечет до обращения к команде приостановки, будет создано исключение.  
  
###  <a name="UsingHTML5ControlsCodedUITestsVideo"></a> Элемент управления видео  
 Действия **элемента управления видео** на элементе управления видео HTML5 правильно записываются и воспроизводятся.  
  
 ![Элемент управления видео HTML5](../test/media/codedui_html5_video.png "CodedUI_HTML5_Video")  
  
|Действие|Запись|Созданный код|  
|------------|---------------|--------------------|  
|**Воспроизведение видео**<br /><br /> Непосредственно из элемента управления или в контекстном меню элемента управления.|Воспроизведение видео \<название> от 00:00:00|HtmlVideo.Play(TimeSpan)|  
|**Переход к определенному моменту времени в видео**|Переход в видео \<название> к 00:01:48|HtmlVideo.Seek(TimeSpan)|  
|**Приостановка видео**<br /><br /> Непосредственно из элемента управления или в контекстном меню элемента управления.|Приостановка видео \<название> на 00:01:53|HtmlVideo.Pause(TimeSpan)|  
|**Отключение звука видео**<br /><br /> Непосредственно из элемента управления или в контекстном меню элемента управления.|Отключение звука видео \<название>|HtmlVideo.Mute()|  
|**Включение звука видео**<br /><br /> Непосредственно из элемента управления или в контекстном меню элемента управления.|Включение звука видео \<название>|HtmlVideo.Unmute()|  
|**Изменение громкости звука видео**|Установка громкости видео \<название> на 79 %||  
  
 Все свойства HtmlAudio доступны для HtmlVideo. Кроме того, также доступны следующие три свойства. На все можно добавить утверждение.  
  
```  
string Poster  
string VideoHeight  
string VideoWidth  
  
```  
  
 **Свойства поиска:** Свойства поиска для `HtmlVideo` равны `Id`, `Name` и `Title`.  
  
 **Свойства фильтра:** Свойства фильтра для `HtmlVideo` равны `Src`, `Poster`, `Class`, `ControlDefinition` и `TagInstance`.  
  
> [!NOTE]
>  Если необходимо перемотать видео вперед или назад, используя метки -30s или +30s, данные будут использоваться для перехода к соответствующему времени.  
  
###  <a name="UsingHTML5ControlsCodedUITestsSlider"></a> Slider  
 Действия **элемента управления Slider** на элементе управления Slider HTML5 правильно записываются и воспроизводятся.  
  
 ![Элемент управления Slider HTML5](../test/media/codedui_html5_slider.png "CodedUI_HTML5_Slider")  
  
|Действие|Запись|Созданный код|  
|------------|---------------|--------------------|  
|**Задать положение ползунка**|Задать положение \<x> ползунку \<название>|HtmlSlider.ValueAsNumber=\<x>|  
  
 Следующие свойства доступны для HtmlSlider и на все можно добавить утверждение:  
  
```  
string Disabled  
string Max  
string Min  
string Required  
string Step  
string ValueAsNumber  
```  
  
###  <a name="UsingHTML5ControlsCodedUITestsProgressbar"></a> ProgressBar  
 **Элемент управления ProgreesBar:** с элементом управления ProgressBar нельзя взаимодействовать. Вы можете добавить утверждения о свойствах `Value` и `Max` этого элемента управления.  

 ![Элемент управления HTML5 ProgressBar](../test/media/codedui_html5_progressbar.png "CodedUI_HTML5_ProgressBar")  

## <a name="see-also"></a>См. также

[Элементы HTML](http://go.microsoft.com/fwlink/?LinkID=232441)  
[Использование модели автоматизации пользовательского интерфейса для тестирования кода](../test/use-ui-automation-to-test-your-code.md)  
[Создание закодированных тестов пользовательского интерфейса](../test/use-ui-automation-to-test-your-code.md)  
[Поддерживаемые конфигурации и платформы для закодированных тестов пользовательского интерфейса и записей действий](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)

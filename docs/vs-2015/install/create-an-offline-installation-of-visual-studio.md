---
title: Создание автономной установки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- offline installation
- offline install
- ISO
ms.assetid: 85d65709-42be-449f-9663-914bf1045089
caps.latest.revision: 22
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 197ae2a168f7f14f7d0ea3d9b82b5943c1af82f4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60077944"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Создание автономной установки Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последние версии документации см. в статье [Создание автономной установки Visual Studio](/visualstudio/install/create-an-offline-installation-of-visual-studio) или [Создание сетевой установки Visual Studio](/visualstudio/install/create-a-network-installation-of-visual-studio).

На этой странице описано, как установить Visual Studio 2015, если отсутствует подключение к Интернету. Тем не менее, чтобы выполнить установку "без подключения", сначала необходимо создать макет автономной установки. Для этого необходимо использовать компьютер, который подключен к Интернету. Вот как это делается.

> [!IMPORTANT]
> Если на компьютере, который отключен от сети, установлена ОС Windows 7 SP1 или Windows Server 2008 R2, необходимо ознакомиться с инструкциями, приведенными в разделе [Устранение неполадок с автономной установкой](#BKMK_tshoot) этой статьи.  Эти шаги необходимо выполнить *перед началом* установки Visual Studio 2015.

## <a name="BKMK_Offline"></a> Выполнение автономной установки в качестве процесса установки

#### <a name="to-create-an-offline-installation-layout"></a>Создание макета автономной установки

1. На странице загрузки [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015) необходимо выбрать выпуск Visual Studio, который будет установлен.

2. После загрузки установщика на компьютер выполните команду \<имя исполняемого файла> /layout.

     Например, выполните команду `vs_enterprise.exe /layout D:\VisualStudio2015`

     Чтобы скачать почти все основные пакеты установки, а не только те, которые применимы к компьютеру, на котором выполняется скачивание, можно использовать параметр `/layout`. Такой подход обеспечивает получение файлов, необходимых для запуска этого установщика, на любом компьютере, и может быть полезным, если требуется установить компоненты, которые не были установлены изначально.

3. После выполнения данной команды появится диалоговое окно, в котором можно изменить расположение макета автономной установки.   Затем нажмите кнопку **Загрузка**.

     В случае успешной загрузки пакета вы увидите сообщение **Установка успешно завершена! Все указанные компоненты успешно получены.**

4. Найдите указанную ранее папку. (Например, D:\VisualStudio2015.) Эта папка содержит все, что необходимо скопировать в общее расположение или на установочный носитель.

    > [!CAUTION]
    > В настоящее время пакет SDK для Android не поддерживает автономную установку. Если попытаться установить компоненты пакета SDK для Android на компьютере, который не подключен к Интернету, может произойти сбой установки. Дополнительные сведения см. в подразделе "Устранение неполадок с автономной установкой" этого раздела.

5. Запустите установку из расположения файла или с установочного носителя.

## <a name="updating-an-offline-installation"></a>Обновление автономной установки
 Корпорация Майкрософт выпустила несколько обновлений для Visual Studio 2015. Чтобы обновить установку Visual Studio, загрузите требуемую версию со страницы [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015). Чтобы создать макет автономной установки и с его помощью обновить Visual Studio 2015, выполните шаги, описанные в этом руководстве.

## <a name="BKMK_tshoot"></a> Устранение неполадок с автономной установкой
 При автономной установке из кэша установки могут выводиться предупреждения о невозможности установить некоторые компоненты и пакеты. В таблице ниже приведены возможные решения таких проблем.

| Компонент или пакет | Решение |
|-|-|
| Dotfuscator и Analytics Community Edition версии 5.19.1 (для таких выпусков Visual Studio как Community, Professional и Enterprise, установленных на ОС **Windows 7 SP1** и **Windows Server 2008 R2**) | Если на компьютере, который не подключен к сети, установлена ОС **Windows 7 SP1** или **Windows Server 2008 R2**, то для установки Visual Studio 2015 необходимо выполнить следующие действия.<br /><br /> 1.  Чтобы скачать CTL-файлы, настройте файловый или веб-сервер.<br /><br /> 2.    Перенаправьте URL-адрес автоматического обновления Майкрософт для среды, в которой отсутствует подключение.<br /><br /> Дополнительные сведения см. на сайте TechNet Майкрософт в статье [Configure Trusted Roots and Disallowed Certificates](https://technet.microsoft.com/library/dn265983.aspx) (Настройка доверенных корневых сертификатов и запрещенных сертификатов). |
| Программа установки Android SDK (уровень API) | Для установки пакетов Android SDK (уровень API) требуется подключение к Интернету. Если вы находитесь в сети с ограниченным доступом, при установке Visual Studio необходимо разрешить доступ к следующим URL-адресам:<br /><br /> -   http://dl.google.com:443<br />-   http://dl-ssl.google.com:443<br />-   https://dl-ssl.google.com/android/repository/*<br /> <br />Дополнительные сведения об устранении возможных проблем с параметрами прокси-сервера см. в записи блога [Сбои установки Visual Studio 2015 (программа установки Android SDK) при использовании прокси-сервера](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/). |
| Шаблоны элементов расширяемости Visual Studio<br /><br /> Расширение GitHub для Visual Studio<br /><br /> Инструменты PowerShell для Visual Studio | Если во время установки Visual Studio 2015 отсутствует подключение к Интернету, то для создания макета автономной установки можно использовать отдельный автономный канал. **Примечание.**  В этот отдельный канал включены последние обновления Visual Studio 2015. <br /><br /> Чтобы создать отдельный автономный канал, выполните следующую команду: /layout *Drive:* \VisualStudio2015 /overridefeeduri *URL-to-feed-xml*.<br /><br /> Например, для отдельного автономного канала Visual Studio 2015 Enterprise на английском языке выполните следующие команды.<br /><br /> `vs_enterprise_ENU.exe /layout D:\VisualStudio2015 /overridefeeduri "http://go.microsoft.com/fwlink/?LinkID=785882&clcid0x409"`<br /><br /> Чтобы получить полный список URL-адресов, которые можно использовать для создания отдельного автономного канала на выбранном языке, см. таблицу ниже. |

 Чтобы создать отдельный автономный канал для выбранного языка, используйте следующие URL-адреса и сведения из таблицы, приведенной выше.

|       Язык        |                            URL-адрес                            |
|-----------------------|-----------------------------------------------------------|
| Китайский (упрощенное письмо)  | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x804 |
| Китайский (традиционное письмо) | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x404 |
|         Чешский         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x405 |
|        Немецкий         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x407 |
|        Английский        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x409 |
|        Испанский        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0xC0A |
|        Французский         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x40C |
|        Итальянский        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x410 |
|       Японский        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x411 |
|        Корейский         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x412 |
|        Польский         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x415 |
|      Португальский       | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x416 |
|        Русский        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x419 |
|        Турецкий        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x41F |

## <a name="see-also"></a>См. также раздел

- [Установка Visual Studio](install-visual-studio-2015.md)
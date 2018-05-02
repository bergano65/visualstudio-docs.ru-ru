---
title: Автоматизация установки Visual Studio с помощью файла ответов
description: Сведения о создании файла ответов JSON для автоматизации установки Visual Studio
ms.date: 08/14/2017
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- response file
- automate
- installation
- command-line
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ef060f77a7ac580cb93c93f8e48889b7f19e4fab
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/20/2018
---
# <a name="how-to-define-settings-in-a-response-file"></a>Как определить параметры в файле ответов

При развертывании Visual Studio администраторы могут указать файл ответа, используя параметр `--in`, как показано в следующем примере:

```cmd
vs_enterprise.exe --in customInstall.json
```

Файлы ответов имеют формат [JSON](http://json-schema.org/) и содержат такие же значения, которые задаются аргументами командной строки.  Обычно, если параметр командной строки не принимает аргументов (например, `--quiet`, `--passive` и т. д.), в файле ответов должно содержаться значение true или false.  Если параметр принимает аргумент (например, `--installPath <dir>`), значение в файле ответов должно быть строкой.  Если параметр принимает аргумент и может встречаться в командной строке несколько раз (например, `--add <id>`), значение должно содержать массив строк.

Указанные в командной строке параметры переопределяют значения, заданные в файле ответов, за исключением тех параметров, которые принимают несколько входных значений (например, `--add`). Для таких параметров все значения, переданные в командной строке, объединяются со значениями из файла ответов.

## <a name="setting-a-default-configuration-for-visual-studio"></a>Настройка конфигурации по умолчанию для Visual Studio

Когда вы с помощью команды `--layout` создаете кэш макета сетевой установки, в этом макете создается первоначальный файл `response.json`. При создании частичного макета этот файл ответов содержит рабочие нагрузки и языки, которые были включены в макет.  Когда программа установки запускается из папки макета, она автоматически использует файл response.json, который выбирает рабочие нагрузки и компоненты, включенные в макет.  Пользователи могут по-прежнему выбирать или отменять выбор рабочих нагрузок в пользовательском интерфейсе программы установки перед установкой Visual Studio.

Администраторы, создающие макет, могут изменить файл `response.json` в макете, чтобы задать другие параметры по умолчанию, которые будут предложены пользователям при установке Visual Studio на основе макета.  Например, если администратор хочет по умолчанию устанавливать конкретные рабочие нагрузки и компоненты, он может добавить их в файл `response.json`.

Когда программа установки Visual Studio запускается из папки макета, она _автоматически_ использует файл ответов, содержащийся в этой папке.  Параметр `--in` использовать необязательно.

Вы можете изменить файл `response.json`, созданный в папке автономного макета, чтобы определить настройки по умолчанию для пользователей, выполняющих установку из этого макета.

> [!WARNING]
> Вам нужно обязательно оставить в нем все существующие свойства, которые были определены при создании макета.

Базовый файл `response.json` в макете должен выглядеть примерно так, как представлено ниже, но значения продукта и канала будут соответствовать условиям вашей установки.

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```

При создании или обновлении макета также создается файл response.template.json.  Этот файл содержит все идентификаторы всех рабочих нагрузок, компонентов и языков, которые могут использоваться.  Этот файл предоставляется в виде шаблона для всего содержимого, которое может быть включено в настраиваемую установку.  Администраторы могут использовать этот файл в качестве отправной точки для пользовательского файла ответов.  Просто удалите идентификаторы тех компонентов, которые не нужно устанавливать, и сохраните их в собственном файле ответов.  Не настраивайте файл response.template.json файла, или изменения будут потеряны при каждом обновлении макета.

## <a name="example-layout-response-file-content"></a>Пример содержимого файла ответов в макете

В следующем примере показана установка Visual Studio Enterprise с шестью популярными рабочими нагрузками и компонентами и пользовательским интерфейсом на английском и французском языках. Вы можете использовать этот пример как шаблон, просто изменив список рабочих нагрузок и компонентов на те, которые вы хотите установить.

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise",

  "installPath": "C:\\VS2017",
  "quiet": false,
  "passive": false,
  "includeRecommended": true,
  "norestart": false,

  "addProductLang": [
    "en-US",
    "fr-FR"
    ],

    "add": [
        "Microsoft.VisualStudio.Workload.ManagedDesktop",
        "Microsoft.VisualStudio.Workload.Data",
        "Microsoft.VisualStudio.Workload.NativeDesktop",
        "Microsoft.VisualStudio.Workload.NetWeb",
        "Microsoft.VisualStudio.Workload.Office",
        "Microsoft.VisualStudio.Workload.Universal",
        "Component.GitHub.VisualStudio"
    ]
}
```

## <a name="get-support"></a>Техническая поддержка

Иногда возникают проблемы. При сбое установки Visual Studio см. инструкции по [устранению неполадок и исправлению ошибок установки и обновления Visual Studio 2017](troubleshooting-installation-issues.md). Если описанные выше действия не устраняют проблему, вы можете обратиться к нам за помощью в чате в реальном времени (только на английском языке). Дополнительные сведения см. на [странице поддержки Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Ниже приведены несколько дополнительных вариантов:

* Вы можете сообщить о проблемах с продуктом в корпорацию Майкрософт, используя средство [Сообщить о проблеме](../ide/how-to-report-a-problem-with-visual-studio-2017.md). Оно доступно как в Visual Studio Installer, так и в Visual Studio IDE.
* Вы можете оставить предложение о продукте на форуме [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Вы можете просматривать описания проблем и искать решения в [сообществе разработчиков Visual Studio](https://developercommunity.visualstudio.com/).
* Вы также можете связаться с нами и другими разработчиками Visual Studio, используя [средство для обсуждения Visual Studio в сообществе Gitter](https://gitter.im/Microsoft/VisualStudio). (Требуется учетная запись [GitHub](https://github.com/).)

## <a name="see-also"></a>См. также

* [Идентификаторы рабочих нагрузок и компонентов Visual Studio 2017](workload-and-component-ids.md)

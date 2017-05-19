---
title: "Автоматизация установки Visual Studio с помощью файла ответов | Документация Майкрософт"
description: "{{ЗАПОЛНИТЕЛЬ}}"
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 448C738E-121F-4B64-8CA8-3BC997817A14
author: timsneath
ms.author: tims
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 2c709b5aa90ff4f5f70f0411c7f4f1870d1725d4
ms.contentlocale: ru-ru
ms.lasthandoff: 05/09/2017

---
# <a name="how-to-define-settings-in-a-response-file"></a>Как определить параметры в файле ответов
При развертывании Visual Studio администраторы могут указать файл ответа, используя параметр `--in`, например так:

```
vs_enterprise.exe --in customInstall.json
```

Файлы ответов имеют формат [JSON](http://json-schema.org/) и содержат такие же значения, которые задаются аргументами командной строки.  Обычно, если параметр командной строки не принимает аргументов (например `--quiet`, `--passive` и т.д.), в файле ответов должно содержаться значение true или false.  Если параметр принимает аргумент (например, `--installPath <dir>`), значение в файле ответов должно быть строкой.  Если параметр принимает аргумент и может встречаться в командной строке несколько раз (например, `--add <id>`), значение должно содержать массив строк.

Указанные в командной строке параметры переопределяют значения, заданные в файле ответов, за исключением тех параметров, которые принимают несколько входных значений (например, `--add`). Для таких параметров все значения, переданные в командной строке, объединяются со значениями из файла ответов.

# <a name="setting-a-default-configuration-for-visual-studio"></a>Настройка конфигурации по умолчанию для Visual Studio

Когда вы с помощью команды `--layout` создаете кэш макета сетевой установки, в этом макете создается первоначальный файл `response.json`.

Администраторы, создающие макет, могут изменить файл `response.json` в макете, чтобы задать другие параметры по умолчанию, которые будут предложены пользователям при установке Visual Studio из этого макета.  Например, если администратор хочет по умолчанию устанавливать конкретные рабочие нагрузки и компоненты, он может добавить их в файл `response.json`.

Когда программа установки Visual Studio запускается из папки макета, она _автоматически_ использует файл ответов, содержащийся в этой папке.  Параметр `--in` использовать не обязательно.

Вы можете изменить файл `response.json`, созданный в папке макета автономной установки, чтобы определить настройки по умолчанию для пользователей, выполняющих установку из этого макета. **Но вам нужно обязательно оставить в нем все существующие свойства, которые были определены при создании макета.**

Базовый файл `response.json` в макете будет выглядеть примерно так, как представлено ниже, но значения продукта и канала будут соответствовать условиям вашей установки.

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```

## <a name="example-layout-response-file-content"></a>Пример содержимого файла ответов в макете
Файл из этого примера установит Visual Studio Enterprise с шестью популярными рабочими нагрузками и компонентами и пользовательским интерфейсом на английском и французском языках. Вы можете использовать его как шаблон, просто изменив список рабочих нагрузок и компонентов на те, которые вы хотите установить.

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


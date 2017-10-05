---
title: "Автоматическое применение ключей продуктов при развертывании Visual Studio | Документация Майкрософт"
ms.custom: 
ms.date: 08/14/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: f23906933add1f4706d8786b2950fb3b5d2e6781
ms.openlocfilehash: 1ebf97930f115795139c9e748df7e03523088a21
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Автоматическое применение ключей продуктов при развертывании Visual Studio
Ключ продукта можно применить программным способом в составе сценария, используемого для автоматизации развертывания Visual Studio. Ключи продуктов могут быть заданы на устройстве программно во время установки Visual Studio или после ее завершения.

## <a name="apply-the-license-after-installation"></a>Применение лицензии после установки
 Чтобы активировать установленную версию Visual Studio с помощью ключа продукта, выполните на конечных компьютерах служебную программу `StorePID.exe` в автоматическом режиме. `StorePID.exe` — это служебная программа, которая устанавливается вместе с Visual Studio 2017 в следующем расположении по умолчанию: <br> `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE`

 Запустите `StorePID.exe` с повышенными привилегиями, используя агент System Center или командную строку с повышенными привилегиями. Введите ключ продукта и код продукта Майкрософт (MPC).

>[!IMPORTANT]
> В ключе продукта необходимо указывать дефисы.

 ```
 StorePID.exe [product key including the dashes] [MPC]
 ```

 В следующем примере показано использование командной строки для применения лицензии к Visual Studio 2017 Enterprise, для которой MPC имеет значение 08860, с помощью ключа продукта `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE`, при условии, что установка выполнена в расположение по умолчанию:

 ```cmd
 "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
 ```

 В следующей таблице перечислены коды MPC для каждого выпуска Visual Studio:

| Visual Studio 2013                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Professional 2017 | 08866 |

Если `StorePID.exe` успешно применен к ключу продукта, для параметра `%ERRORLEVEL%` возвращается значение 0. При обнаружении ошибок возвращается один из следующих кодов в зависимости от состояния ошибки:

| Ошибка                     | Код |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

## <a name="see-also"></a>См. также
 * [Установка Visual Studio](../install/install-visual-studio.md)
 * [Создание автономной установки Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)


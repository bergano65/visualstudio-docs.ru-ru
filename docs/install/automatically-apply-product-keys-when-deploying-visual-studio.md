---
title: "Автоматическое применение ключей продуктов при развертывании Visual Studio | Документация Майкрософт"
ms.custom: 
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
caps.latest.revision: 10
author: TerryGLee
ms.author: tglee
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
ms.openlocfilehash: 493ea235a3d89a04a4c6accfa491e622792e4397
ms.contentlocale: ru-ru
ms.lasthandoff: 05/09/2017

---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Автоматическое применение ключей продуктов при развертывании Visual Studio
Ключ продукта можно применить программным способом в составе сценария автоматизации развертывания Visual Studio. Ключи продуктов могут быть заданы на устройстве программно во время установки Visual Studio или после завершения установки.

## <a name="apply-the-license-after-installation"></a>Применение лицензии после установки
 Чтобы активировать установленную версию Visual Studio с помощью ключа продукта, выполните на конечных компьютерах служебную программу `StorePID.exe` в автоматическом режиме. `StorePID.exe` — это служебная программа, которая устанавливается вместе с Visual Studio 2017 в следующем расположении по умолчанию: <br> `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE`

 Запустите `StorePID.exe` с помощью агента System Center или из командной строки с повышенными привилегиями, указав ключ продукта (включая дефисы) и код продукта Майкрософт (MPC). В ключе продукта необходимо указывать дефисы.

 ```
 StorePID.exe [product key including the dashes] [MPC]
 ```

 Это пример командной строки для применения лицензии к Visual Studio 2017 Enterprise, для которой MPC имеет значение 08860, с помощью ключа продукта `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE`, при условии, что установка выполнена в расположение по умолчанию:

 ```cmd
 "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
 ```

 В следующей таблице перечислены коды MPC для каждого выпуска Visual Studio:

| Visual Studio 2013                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Professional 2017 | 08866 |

Если `StorePID.exe` успешно применен к ключу продукта, для параметра `%ERRORLEVEL%` возвращается значение 0. При обнаружении ошибки возвращается код в зависимости от состояния ошибки:

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


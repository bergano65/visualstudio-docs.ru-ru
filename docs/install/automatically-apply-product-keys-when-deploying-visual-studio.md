---
title: "Автоматическое применение ключей продуктов при развертывании Visual Studio | Документация Майкрософт"
ms.custom: 
ms.date: 3/10/2017
ms.reviewer: 
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
translationtype: Human Translation
ms.sourcegitcommit: af9699b63fdfb81a274affb78856817520c38b05
ms.openlocfilehash: 36a774583f5125ecc09210c9ad5da15ec800f870
ms.lasthandoff: 04/03/2017

---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Автоматическое применение ключей продуктов при развертывании Visual Studio
Ключ продукта можно применить программным способом в составе сценария автоматизации развертывания Visual Studio. Ключи продуктов могут быть заданы на устройстве программно во время установки Visual Studio или после завершения установки.  

## <a name="apply-the-license-during-installation"></a>Применение лицензии во время установки  
 Для применения ключа продукта во время установки Visual Studio следует использовать параметр `--productKey`. Этот параметр установки можно использовать вместе с параметром `--quiet parameter`, и тогда Visual Studio для конечного пользователя будет установлена уже лицензированной. Чтобы использовать параметр `--productKey`, откройте командную строку. Запустите программу установки (например, vs_enterprise.exe или vs_professional.exe) и задайте для параметра `--productKey` значение ключа продукта (25 символов) с дефисами или без дефисов:  

 Это пример команды для установки Visual Studio 2015 Enterprise с ключом продукта AAAAABBBBBCCCCCDDDDDEEEEEEE:  

 `vs_enterprise.exe [any other setup parameters] --productKey AAAAABBBBBCCCCCDDDDDDEEEEEE`  

## <a name="apply-the-license-after-installation"></a>Применение лицензии после установки  
 Активировать установленную версию Visual Studio с помощью ключа продукта можно путем запуска служебной программы storePID.exe на конечных компьютерах в автоматическом режиме. StorePID.exe – это служебная программа, которая устанавливается вместе с Visual Studio по адресу **\<диск>:\\\Program Files (x86)\Microsoft Visual Studio 15.0\Common7\IDE\StorePID.exe**.  

 Запустите storePID.exe с повышенными привилегиями либо с помощью агента System Center, либо из командной строки с повышенными привилегиями, указав ключ продукта (включая дефисы) и код продукта Майкрософт (MPC). В ключе продукта необходимо указывать дефисы!  

 `StorePID.exe [product key including the dashes] [MPC]`  

 Здесь приводится пример команды для установки Visual Studio 2017 Enterprise с кодом MPC 08860 и ключом продукта AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE:  

 `C:\Program Files (x86)\Microsoft Visual Studio 15.0\Common7\IDE\StorePID.exe AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860`  

 В следующей таблице перечислены коды MPC для каждого выпуска Visual Studio:  

|Visual Studio 2013 | MPC |  
|---------------------------|---------|
|Visual Studio Enterprise 2017|08860|  
|Visual Studio Professional 2017|08862|  
|Visual Studio Test Professional 2017|08866|
|Visual Studio Enterprise|07060|  
|Visual Studio Professional 2015|07062|  
|Visual Studio Test Professional 2015|07066|  
|Visual Studio Ultimate 2013|06181|  
|Visual Studio Premium 2013|06191|  
|Visual Studio Professional 2013|06177|  
|Visual Studio Test Professional 2013|06194|  

Если StorePID.exe успешно применены ключ продукта, возвращается 0. В случае возникновения ошибки возвращается число в диапазоне от 1 до 6.  

## <a name="see-also"></a>См. также  
 * [Установка Visual Studio](../install/install-visual-studio.md)
 * [Создание автономной установки Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)


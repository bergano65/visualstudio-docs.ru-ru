---
title: Подписание пакетов VSIX (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17179c35496fc19322c5bb951f4d04bc28e5d7bc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700091"
---
# <a name="signing-vsix-packages"></a>Подписывание пакетов VSIX
Сборки расширений не должны быть подписаны, прежде чем они смогут работать в Visual Studio, но это хорошая практика, чтобы сделать это.

 Если вы хотите обеспечить ваше расширение и убедиться, что оно не было подделано, вы можете добавить цифровую подпись в пакет VSIX. При подписании VSIX установщик VSIX будет отображать сообщение о подписании, а также дополнительную информацию о самой подписи. Если содержимое VSIX было изменено, а VSIX не подписан снова, установщик VSIX покажет, что подпись недействительна. Установка не остановлена, но пользователь предупрежден.

> [!IMPORTANT]
> Начиная с Visual Studio 2015, пакеты VSIX, подписанные с использованием чего-либо, кроме шифрования SHA256, будут идентифицированы как имеющие недействительную подпись. Установка VSIX не заблокирована, но пользователь будет предупрежден.

## <a name="signing-a-vsix-with-vsixsigntool"></a>Подписание VSIX с VSIXSignTool
 Существует SHA256 шифрования подписания инструмент, доступный от [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) на nuget.org на [VsixSignTool](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).

#### <a name="to-use-the-vsixsigntool"></a>Использовать VSIXSignTool

1. Добавьте vSIX в проект.

2. Нажмите правой кнопкой мыши на узло проекта в Solution Explorer, выбрав **добавить &#124; управлять пакетами NuGet.**  Для получения дополнительной информации о NuGet и добавлении пакетов NuGet смотрите темы [uI документации NuGet](/NuGet) и [менеджера пакетов.](/NuGet/Tools/Package-Manager-UI)

3. Поиск VSIXSignTool от VisualStudioEx, и установите пакет NuGet.

4. Теперь вы можете запустить VSIXSignTool из локального расположения пакетов проекта. Обратитесь к командной строке инструмента помочь для вашего сценария подписания (VSIXSignTool.exe /?).

   Например, подписать с защищенным паролем файл сертификата:

   VSIXSignTool.exe знак \</f certfile \<> \</p пароль> VSIXfile>

## <a name="see-also"></a>См. также
- [Доставка расширений Visual Studio](../extensibility/shipping-visual-studio-extensions.md)

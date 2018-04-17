---
title: Подписывание пакетов VSIX | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 84166ed96fb49567f4ede3e8e0c4b7e8ba3cc814
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="signing-vsix-packages"></a>Подписывание пакетов VSIX
Расширения сборок не обязательно должны быть подпись перед их работу в Visual Studio, но это рекомендуется делать это.  
  
 Если вы хотите защитить модуля и убедитесь, что оно не было изменено, можно добавить цифровую подпись для пакета VSIX. При подписании VSIX установщик VSIX будет выведено сообщение, указывающее, что он подписан, а также дополнительные сведения о саму подпись. Если содержимое VSIX были изменены, а VSIX снова не подписана, установщик VSIX покажет подпись не является допустимым. Установка не остановлен, но пользователь получает предупреждение.  
  
> [!IMPORTANT]
>  Начиная с 2015 подписывается с помощью ничего, кроме SHA256 шифрования пакетов VSIX указывается имеет недопустимую подпись. Установка VSIX не блокируется, но пользователь появится предупреждение.  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>Подписи VSIX с VSIXSignTool  
 Нет SHA256 шифрование, подписывание средство, доступное из [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) на nuget.org на [VsixSignTool](http://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).  
  
#### <a name="to-use-the-vsixsigntool"></a>Чтобы использовать VSIXSignTool  
  
1.  Добавление в проект в VSIX.  
  
2.  Щелкните правой кнопкой мыши узел проекта в обозревателе решений, выбрав **добавить &#124; управление пакетами NuGet**.  Дополнительные сведения о NuGet и добавление пакетов NuGet см. в разделе [документации по NuGet](/NuGet) и [пользовательского интерфейса диспетчера пакетов](/NuGet/Tools/Package-Manager-UI) разделы.  
  
3.  Поиск VSIXSignTool из VisualStudioExtensibility и установите пакет NuGet.  
  
4.  Теперь можно запустить VSIXSignTool из расположения локальных пакетов проекта. Обратитесь к справке средства командной строки для подписывания сценария (VSIXSignTool.exe /?).  
  
 Например, для входа с паролем защищенные файл сертификата:  
  
 /F VSIXSignTool.exe входа \<certfile > /p \<пароль > \<VSIXfile >  
  
## <a name="see-also"></a>См. также  
 [Доставка расширений Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
---
title: "DECRYPTBYKEY (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DecryptByKey_TSQL
- DECRYPTBYKEY
dev_langs:
- TSQL
helpviewer_keywords:
- symmetric keys [SQL Server], DecryptByKey function
- decryption [SQL Server], keys
- decryption [SQL Server], symmetric keys
- DECRYPTBYKEY function
ms.assetid: 6edf121f-ac62-4dae-90e6-6938f32603c9
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: a1275be81fdf2a8405d0f744da962c3cf874eea2
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="decryptbykey-transact-sql"></a>DECRYPTBYKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Расшифровывает данные с помощью симметричного ключа.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DecryptByKey ( { 'ciphertext' | @ciphertext }   
    [ , add_authenticator, { authenticator | @authenticator } ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *ciphertext*  
 Данные, зашифрованные с помощью ключа. Аргумент *ciphertext* имеет тип **varbinary**.  
  
 **@ciphertext**  
 Переменная типа **varbinary**. Содержит данные, которые были зашифрованы с помощью ключа.  
  
 *add_authenticator*  
 Указывает, была ли структура проверки подлинности зашифровано вместе с неформатированным текстом. Должно быть равно значению, переданному функции EncryptByKey при шифровании данных. Аргумент *add_authenticator* имеет тип **int**.  
  
 *authenticator*  
 Данные, для которых формируется средство проверки подлинности. Значение аргумента должно совпадать со значением, заданным функции EncryptByKey. Аргумент *authenticator* имеет тип **sysname**.  
  
 **@authenticator**  
 Переменная, содержащая сведения, из которых формируются данные для проверки подлинности. Значение аргумента должно совпадать со значением, заданным функции EncryptByKey.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Переменная типа **varbinary** с максимальным размером 8000 байт.  
  
## <a name="remarks"></a>Remarks  
 В функции DecryptByKey используется симметричный ключ. Этот симметричный ключ должен быть открыт уже в базе данных. Одновременно могут быть открыты несколько ключей. Открывать ключ непосредственно перед раскодированием необязательно.  
  
 Симметричное кодирование и декодирование осуществляется относительно быстро и подходит для работы с большими объемами данных.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо, чтобы симметричный ключ был открыт в текущем сеансе. Дополнительные сведения см. в статье [OPEN SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/open-symmetric-key-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-decrypting-by-using-a-symmetric-key"></a>A. Декодирование с помощью симметричного ключа  
 Следующий пример иллюстрирует декодирование зашифрованного текста с помощью симметричного ключа.  
  
```  
-- First, open the symmetric key with which to decrypt the data.  
OPEN SYMMETRIC KEY SSN_Key_01  
   DECRYPTION BY CERTIFICATE HumanResources037;  
GO  
  
-- Now list the original ID, the encrypted ID, and the   
-- decrypted ciphertext. If the decryption worked, the original  
-- and the decrypted ID will match.  
SELECT NationalIDNumber, EncryptedNationalID   
    AS 'Encrypted ID Number',  
    CONVERT(nvarchar, DecryptByKey(EncryptedNationalID))   
    AS 'Decrypted ID Number'  
    FROM HumanResources.Employee;  
GO  
```  
  
### <a name="b-decrypting-by-using-a-symmetric-key-and-an-authenticating-hash"></a>Б. Декодирование с помощью симметричного ключа и цифровой подписи  
 Следующий пример иллюстрирует расшифровку данных, зашифрованных с помощью средства проверки подлинности.  
  
```  
-- First, open the symmetric key with which to decrypt the data  
OPEN SYMMETRIC KEY CreditCards_Key11  
   DECRYPTION BY CERTIFICATE Sales09;  
GO  
  
-- Now list the original card number, the encrypted card number,  
-- and the decrypted ciphertext. If the decryption worked,   
-- the original number will match the decrypted number.  
SELECT CardNumber, CardNumber_Encrypted   
    AS 'Encrypted card number', CONVERT(nvarchar,  
    DecryptByKey(CardNumber_Encrypted, 1 ,   
    HashBytes('SHA1', CONVERT(varbinary, CreditCardID))))   
    AS 'Decrypted card number' FROM Sales.CreditCard;  
GO  
  
```  
  
## <a name="see-also"></a>См. также:  
 [ENCRYPTBYKEY (Transact-SQL)](../../t-sql/functions/encryptbykey-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [ALTER SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/alter-symmetric-key-transact-sql.md)   
 [DROP SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/drop-symmetric-key-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Выбор алгоритма шифрования](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
  
  

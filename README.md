import pandas as pd

# 알파벳을 6자리 이진수로 매핑
alphabet_to_binary = {
    'A': '000001', 'B': '000010', 'C': '000011', 'D': '000100', 'E': '000101',
    'F': '000110', 'G': '000111', 'H': '001000', 'I': '001001', 'J': '001010',
    'K': '001011', 'L': '001100', 'M': '001101', 'N': '001110', 'O': '001111',
    'P': '010000', 'Q': '010001', 'R': '010010', 'S': '010011', 'T': '010100',
    'U': '010101', 'V': '010110', 'W': '010111', 'X': '011000', 'Y': '011001',
    'Z': '011010'
}

# 암호화 규칙
encryption_rules = {
    ('0', '0'): '0',
    ('1', '1'): '1',
    ('1', '0'): '2',
    ('0', '1'): '3'
}

# 텍스트를 이진수로 변환
def text_to_binary(text):
    binary_str = ''
    for char in text.upper():
        if char in alphabet_to_binary:
            binary_str += alphabet_to_binary[char]
    return binary_str

# 이진수를 암호화
def encrypt_binary(binary_str):
    encrypted_code = ''
    for i in range(0, len(binary_str), 2):
        chunk = binary_str[i:i+2]
        if len(chunk) == 2:
            encrypted_code += encryption_rules[(chunk[0], chunk[1])]
    return encrypted_code

# 메인 함수
def main():
    # 사용자로부터 영어 텍스트 입력 받기
    text = input("암호화할 영어 텍스트를 입력하세요: ")
    
    # 텍스트를 이진수로 변환
    binary_str = text_to_binary(text)
    
    # 이진수를 암호화
    encrypted_code = encrypt_binary(binary_str)
    
    # 결과 출력
    print("\n암호화 결과:")
    print(encrypted_code)

# 프로그램 실행
if __name__ == "__main__":
    main()

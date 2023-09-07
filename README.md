# bank_web_project


USE bank_db;

CREATE TABLE IF NOT EXISTS Customers (
    customer_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    phone_number VARCHAR(15) NOT NULL,
    address VARCHAR(255) NOT NULL,
    date_of_birth DATE NOT NULL,
    gender VARCHAR(10),
    occupation VARCHAR(50),
    password VARCHAR(100) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE IF NOT EXISTS Accounts (
    account_id INT AUTO_INCREMENT PRIMARY KEY,
    account_number VARCHAR(20) UNIQUE NOT NULL,
    customer_id INT NOT NULL,
    account_type VARCHAR(50) NOT NULL,
    balance DECIMAL(10, 2) DEFAULT 0.00,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (customer_id) REFERENCES Customers(customer_id)
);

CREATE TABLE IF NOT EXISTS FinancialProducts (
    product_id INT AUTO_INCREMENT PRIMARY KEY,
    product_name VARCHAR(100) NOT NULL,
    product_type VARCHAR(50) NOT NULL,
    interest_rate DECIMAL(5, 2) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE IF NOT EXISTS Admins (
    admin_id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) UNIQUE NOT NULL,
    password VARCHAR(100) NOT NULL,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);







-- 데이터베이스 선택
USE bank_db;

-- Customers 테이블 생성 (이미 존재하면 생략)
CREATE TABLE IF NOT EXISTS Customers (
    customer_id INT AUTO_INCREMENT PRIMARY KEY, -- 고객 ID (자동 증가)
    name VARCHAR(100) NOT NULL, -- 이름
    email VARCHAR(100) UNIQUE NOT NULL, -- 이메일 (고유한 값, 필수)
    phone_number VARCHAR(15) NOT NULL, -- 전화번호 (필수)
    address VARCHAR(255) NOT NULL, -- 주소 (필수)
    date_of_birth DATE NOT NULL, -- 생년월일 (필수)
    gender VARCHAR(10), -- 성별
    occupation VARCHAR(50), -- 직업 (NULL 허용)
    password VARCHAR(100) NOT NULL, -- 비밀번호 (필수)
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP -- 생성 일시 (자동 생성)
);

-- Accounts 테이블 생성 (이미 존재하면 생략)
CREATE TABLE IF NOT EXISTS Accounts (
    account_id INT AUTO_INCREMENT PRIMARY KEY, -- 계좌 ID (자동 증가)
    account_number VARCHAR(20) UNIQUE NOT NULL, -- 계좌 번호 (고유한 값, 필수)
    customer_id INT NOT NULL, -- 고객 ID (필수)
    account_type VARCHAR(50) NOT NULL, -- 계좌 유형 (필수)
    balance DECIMAL(10, 2) DEFAULT 0.00, -- 잔액 (기본값 0.00)
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP, -- 생성 일시 (자동 생성)
    FOREIGN KEY (customer_id) REFERENCES Customers(customer_id) -- 외래 키 (Customers 테이블과 연결)
);

-- FinancialProducts 테이블 생성 (이미 존재하면 생략)
CREATE TABLE IF NOT EXISTS FinancialProducts (
    product_id INT AUTO_INCREMENT PRIMARY KEY, -- 금융 상품 ID (자동 증가)
    product_name VARCHAR(100) NOT NULL, -- 상품명 (필수)
    product_type VARCHAR(50) NOT NULL, -- 상품 유형 (필수)
    interest_rate DECIMAL(5, 2) NOT NULL, -- 이자율 (필수)
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP -- 생성 일시 (자동 생성)
);

-- Admins 테이블 생성 (비밀번호 열 추가)
CREATE TABLE IF NOT EXISTS Admins (
    admin_id INT AUTO_INCREMENT PRIMARY KEY, -- 관리자 ID (자동 증가)
    username VARCHAR(50) UNIQUE NOT NULL, — 사용자 이름 (고유한 값, 필수)
    password VARCHAR(100) NOT NULL, — 비밀번호 (필수)
    name VARCHAR(100) NOT NULL, — 이름 (필수)
    email VARCHAR(100) UNIQUE NOT NULL, — 이메일 (고유한 값, 필수)
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP — 생성 일시 (자동 생성)
);

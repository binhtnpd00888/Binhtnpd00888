# Binhtnpd00888
-- Created by Vertabelo (http://vertabelo.com)
-- Script type: create
-- Scope: [tables, references, sequences, views, procedures]
-- Generated at Sun Mar 01 14:38:15 UTC 2015




-- tables
-- Table: CHi_Tiet_Hoa_Don
CREATE TABLE CHi_Tiet_Hoa_Don (
    ID_CHi_Tiet_Hoa_Don int  NOT NULL,
    Nguoi_Danh_Gia varchar(255)  NOT NULL,
    ID_CHi_Tiet_Hoa_Don_01 int  NOT NULL,
    CONSTRAINT CHi_Tiet_Hoa_Don_pk PRIMARY KEY (ID_CHi_Tiet_Hoa_Don)
)
;





-- Table: Hoa_Don
CREATE TABLE Hoa_Don (
    ID_Hoa_Don int  NOT NULL,
    Nguoi_Ki_HD char(10)  NOT NULL,
    Hoa_Don_Loai char(255)  NOT NULL,
    Noi_Dung_HD varchar(255)  NOT NULL,
    ID_Hoa_Don_01 int  NOT NULL,
    CONSTRAINT Hoa_Don_pk PRIMARY KEY (ID_Hoa_Don)
)
;





-- Table: Khachhang
CREATE TABLE Khachhang (
    ID_KhachHang int  NOT NULL,
    Ho_Va_Ten Nvarchar(15)  NOT NULL,
    GIOI_TINH Nvarchar(5)  NOT NULL,
    DIEN_THOAI nvarchar(15)  NOT NULL,
    DIA_CHI Nvarchar(15)  NOT NULL,
    ID_Khachhang int  NOT NULL,
    San_Pham_ID_San_Pham int  NOT NULL,
    CONSTRAINT Khachhang_ak_1 UNIQUE (ID_KhachHang),
    CONSTRAINT Khachhang_pk PRIMARY KEY (ID_KhachHang)
)
;





-- Table: Loai_SanPham
CREATE TABLE Loai_SanPham (
    ID_San_Pham01 int  NOT NULL,
    TEN_San_pham char(12)  NOT NULL,
    Gia_Tien char(12)  NOT NULL,
    Suat_Su char(12)  NOT NULL,
    ID_Loai_san_pham int  NOT NULL,
    CONSTRAINT Loai_SanPham_pk PRIMARY KEY (ID_San_Pham01)
)
;





-- Table: San_Pham
CREATE TABLE San_Pham (
    ID_San_Pham int  NOT NULL,
    Loai_San_Pham Nvarchar(15)  NOT NULL,
    Gia_Tien Nvarchar(15)  NOT NULL,
    ID_San_Pham_1 int  NOT NULL,
    CONSTRAINT San_Pham_pk PRIMARY KEY (ID_San_Pham)
)
;









-- foreign keys
-- Reference:  Khachhang_San_Pham (table: Khachhang)


ALTER TABLE Khachhang ADD CONSTRAINT Khachhang_San_Pham 
    FOREIGN KEY (San_Pham_ID_San_Pham)
    REFERENCES San_Pham (ID_San_Pham)
;

-- Reference:  client_purchase (table: Loai_SanPham)


ALTER TABLE Loai_SanPham ADD CONSTRAINT client_purchase 
    FOREIGN KEY (Gia_Tien)
    REFERENCES Khachhang (ID_KhachHang)
;

-- Reference:  product_category_product (table: Hoa_Don)


ALTER TABLE Hoa_Don ADD CONSTRAINT product_category_product 
    FOREIGN KEY (Nguoi_Ki_HD)
    REFERENCES CHi_Tiet_Hoa_Don (ID_CHi_Tiet_Hoa_Don)
;

-- Reference:  product_purchase_item (table: San_Pham)


ALTER TABLE San_Pham ADD CONSTRAINT product_purchase_item 
    FOREIGN KEY (Gia_Tien)
    REFERENCES Hoa_Don (ID_Hoa_Don)
;

-- Reference:  purchase_purchase_item (table: San_Pham)


ALTER TABLE San_Pham ADD CONSTRAINT purchase_purchase_item 
    FOREIGN KEY (Loai_San_Pham)
    REFERENCES Loai_SanPham (ID_San_Pham01)
;





-- End of file.

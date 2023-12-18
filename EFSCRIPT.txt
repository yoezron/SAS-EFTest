---
API: 2.1
OpenSesame: 3.3.12
Platform: nt
---
set width 1920
set uniform_coordinates yes
set title "New experiment"
set subject_parity even
set subject_nr 0
set start EFARMYTASK
set sound_sample_size -16
set sound_freq 48000
set sound_channels 2
set sound_buf_size 1024
set sampler_backend legacy
set round_decimals 2
set pygame_window_pos auto
set pygame_window_frame yes
set pygame_hwsurface yes
set pygame_doublebuf yes
set mouse_backend legacy
set keyboard_backend legacy
set height 1080
set fullscreen no
set form_clicks no
set foreground black
set font_underline no
set font_size 18
set font_italic no
set font_family arabic
set font_bold no
set experiment_path "E:\\OneDrive - UGM 365\\0. SAS Project\\EF TEST"
set disable_garbage_collection yes
set description "The main experiment item"
set coordinates uniform
set compensation 0
set color_backend legacy
set clock_backend legacy
set canvas_backend legacy
set background white

define loop Aba_aba
	set source_file ""
	set source table
	set repeat 1
	set order sequential
	set description "Repeatedly runs another item"
	set cycles 5
	set continuous no
	set break_if_on_first yes
	set break_if never
	setcycle 0 abaaba "Siap?"
	setcycle 0 durasi 1500
	setcycle 0 color black
	setcycle 1 abaaba 1
	setcycle 1 durasi 1000
	setcycle 1 color red
	setcycle 2 abaaba 2
	setcycle 2 durasi 1000
	setcycle 2 color orange
	setcycle 3 abaaba 3
	setcycle 3 durasi 1000
	setcycle 3 color yellow
	setcycle 4 abaaba "Mulai!"
	setcycle 4 durasi 1500
	setcycle 4 color green
	run SEQ_ABA2

define sketchpad Banner_GNG
	set duration keypress
	set description "Displays stimuli"
	draw textline center=1 color=white font_bold=yes font_family=serif font_italic=no font_size=30 html=yes show_if=always text="Klik 'Spasi' untuk memulai!" x=0 y=192 z_index=0
	draw image center=1 file="gonogo.png" scale=1 show_if=always x=0 y=0 z_index=0

define sketchpad Banner_WM1
	set duration keypress
	set description "Displays stimuli"
	draw textline center=1 color=white font_bold=yes font_family=serif font_italic=no font_size=30 html=yes show_if=always text="Klik Spasi untuk Memulai!" x=0 y=192 z_index=0
	draw image center=1 file="speed.png" scale=1.0 show_if=always x=0 y=0 z_index=0

define sketchpad Banner_WM2
	set duration keypress
	set description "Displays stimuli"
	draw textline center=1 color=white font_bold=yes font_family=serif font_italic=no font_size=30 html=yes show_if=always text="Klik 'Spasi' untuk memulai!" x=0 y=192 z_index=0
	draw image center=1 file="energy.png" scale=1.0 show_if=always x=0 y=0 z_index=0

define sketchpad Banner_WM2_1
	set duration keypress
	set description "Displays stimuli"
	draw textline center=1 color="#ffffff" font_bold=no font_family=serif font_italic=no font_size=20 html=yes show_if=always text="Klik 'Spasi' untuk memulai..." x=0 y=224 z_index=0
	draw image center=1 file="capacity.png" scale=1.0 show_if=always x=0 y=0 z_index=0

define sequence EFARMYTASK
	set flush_keyboard yes
	set description "Runs a number of items in sequence"
	run welcome always
	run new_form_text_input always
	run Instruksi_Umum always
	run wait always
	run WM_1 always
	run WM_2 always
	run WM_3 always
	run GNG always
	run End always

define sketchpad End
	set duration keypress
	set description "Displays stimuli"
	draw image center=1 file="endpage.png" scale=1.0 show_if=always x=0 y=0 z_index=0

define loop GNG
	set source_file ""
	set source table
	set repeat 1
	set order random
	set description "Repeatedly runs another item"
	set cycles 1
	set continuous no
	set break_if_on_first yes
	set break_if never
	setcycle 0 test_session "go no go task"
	run SEQ_4

define sketchpad Instruksi_GNG
	set duration keypress
	set description "Displays stimuli"
	draw image center=1 file="Instruksi_GONOGO.png" scale=1 show_if=always x=0 y=0 z_index=0

define sketchpad Instruksi_Umum
	set duration keypress
	set description "Displays stimuli"
	draw image center=1 file="Instruksi Umum.png" scale=0.9500000000000001 show_if=always x=0 y=0 z_index=0

define sketchpad Instruksi_WM1
	set duration keypress
	set description "Displays stimuli"
	draw image center=1 file="Instruksi WM1.png" scale=1.0 show_if=always x=0 y=0 z_index=0

define sketchpad Instruksi_WM2
	set duration keypress
	set description "Displays stimuli"
	draw image center=1 file="Instruksi2.png" scale=1.0 show_if=always x=0 y=0 z_index=0

define sketchpad Instruksi_WM3
	set duration keypress
	set description "Displays stimuli"
	draw image center=1 file="Instruksi_WM3.png" scale=1.0 show_if=always x=0 y=0 z_index=0

define sequence SEQ_1
	set flush_keyboard yes
	set description "Runs a number of items in sequence"
	run Banner_WM1 always
	run wait always
	run Instruksi_WM1 always
	run wait always
	run Aba_aba always
	run WM_1_Ganjil "[subject_parity] = odd"
	run WM_1_Genap "[subject_parity] = even"
	run new_feedback always

define sequence SEQ_2
	set flush_keyboard yes
	set description "Runs a number of items in sequence"
	run Banner_WM2 always
	run wait always
	run Instruksi_WM2 always
	run wait always
	run Aba_aba always
	run WM_2_Ganjil "[subject_parity] = odd"
	run WM_2_Genap "[subject_parity] = even"
	run new_feedback always

define sequence SEQ_3
	set flush_keyboard yes
	set description "Runs a number of items in sequence"
	run Banner_WM2_1 always
	run wait always
	run Instruksi_WM3 always
	run wait always
	run Aba_aba always
	run inline_varstotal always
	run WM_3_Ganjil "[subject_parity] = odd"
	run WM_3_Genap "[subject_parity] = even"
	run feedback_capacity always
	run log_score always

define sequence SEQ_4
	set flush_keyboard yes
	set description "Runs a number of items in sequence"
	run Banner_GNG always
	run wait always
	run Instruksi_GNG always
	run wait always
	run Aba_aba always
	run gonogoarmy always
	run new_feedback always

define sequence SEQ_ABA2
	set flush_keyboard yes
	set description "Runs a number of items in sequence"
	run pad_aba2 always

define loop WM_1
	set source_file ""
	set source table
	set repeat 1
	set order random
	set description "Repeatedly runs another item"
	set cycles 1
	set continuous no
	set break_if_on_first yes
	set break_if never
	setcycle 0 test_session speed_test
	run SEQ_1

define loop WM_1_Ganjil
	set source_file ""
	set source table
	set repeat 1
	set order sequential
	set description "Repeatedly runs another item"
	set cycles 54
	set continuous no
	set break_if_on_first yes
	set break_if never
	setcycle 0 correct_response space
	setcycle 0 shape_target 3
	setcycle 0 shape_distractor 13
	setcycle 0 tar_pos 160
	setcycle 0 dis_pos -160
	setcycle 0 time 50000
	setcycle 0 dialog "Ingat kedua gambar berikut beserta posisinya!"
	setcycle 0 dialog2 "Klik spasi untuk melanjutkan!"
	setcycle 0 y 0
	setcycle 1 correct_response 1
	setcycle 1 shape_target 13
	setcycle 1 shape_distractor 4
	setcycle 1 tar_pos -160
	setcycle 1 dis_pos 160
	setcycle 1 time 50000
	setcycle 1 dialog "Gambar di nomor manakah yang ada pada gambar sebelumnya?"
	setcycle 1 dialog2 "Klik angka 1 atau angka 2 pada keyboard!"
	setcycle 1 y 0
	setcycle 2 correct_response 2
	setcycle 2 shape_target 4
	setcycle 2 shape_distractor 10
	setcycle 2 tar_pos 160
	setcycle 2 dis_pos -160
	setcycle 2 time 50000
	setcycle 2 dialog "Ingat gambar sebelumnya! Gambar di nomor manakah yang ada pada gambar sebelumnya?"
	setcycle 2 dialog2 "Klik angka 1 atau angka 2 pada keyboard!"
	setcycle 2 y 0
	setcycle 3 correct_response 2
	setcycle 3 shape_target 10
	setcycle 3 shape_distractor 1
	setcycle 3 tar_pos 160
	setcycle 3 dis_pos -160
	setcycle 3 time 50000
	setcycle 3 dialog "Sudah mengerti cara mainnya? Setelah ini anda harus menjawab dengan cepat!"
	setcycle 3 dialog2 "Klik angka 1 atau angka 2 pada keyboard!"
	setcycle 3 y 0
	setcycle 4 correct_response 2
	setcycle 4 shape_target 1
	setcycle 4 shape_distractor 12
	setcycle 4 tar_pos 160
	setcycle 4 dis_pos -160
	setcycle 4 time 1200
	setcycle 4 dialog ""
	setcycle 4 dialog2 ""
	setcycle 4 y 0
	setcycle 5 correct_response 1
	setcycle 5 shape_target 12
	setcycle 5 shape_distractor 1
	setcycle 5 tar_pos -160
	setcycle 5 dis_pos 160
	setcycle 5 time 1200
	setcycle 5 dialog ""
	setcycle 5 dialog2 ""
	setcycle 5 y 0
	setcycle 6 correct_response 2
	setcycle 6 shape_target 1
	setcycle 6 shape_distractor 10
	setcycle 6 tar_pos 160
	setcycle 6 dis_pos -160
	setcycle 6 time 1200
	setcycle 6 dialog ""
	setcycle 6 dialog2 ""
	setcycle 6 y 0
	setcycle 7 correct_response 1
	setcycle 7 shape_target 10
	setcycle 7 shape_distractor 3
	setcycle 7 tar_pos -320
	setcycle 7 dis_pos -32
	setcycle 7 time 1200
	setcycle 7 dialog ""
	setcycle 7 dialog2 ""
	setcycle 7 y 64
	setcycle 8 correct_response 1
	setcycle 8 shape_target 3
	setcycle 8 shape_distractor 14
	setcycle 8 tar_pos 32
	setcycle 8 dis_pos 320
	setcycle 8 time 1200
	setcycle 8 dialog ""
	setcycle 8 dialog2 ""
	setcycle 8 y 64
	setcycle 9 correct_response 2
	setcycle 9 shape_target 14
	setcycle 9 shape_distractor 1
	setcycle 9 tar_pos 160
	setcycle 9 dis_pos -160
	setcycle 9 time 1200
	setcycle 9 dialog ""
	setcycle 9 dialog2 ""
	setcycle 9 y 0
	setcycle 10 correct_response 1
	setcycle 10 shape_target 1
	setcycle 10 shape_distractor 14
	setcycle 10 tar_pos 32
	setcycle 10 dis_pos 320
	setcycle 10 time 1200
	setcycle 10 dialog ""
	setcycle 10 dialog2 ""
	setcycle 10 y 64
	setcycle 11 correct_response 2
	setcycle 11 shape_target 14
	setcycle 11 shape_distractor 4
	setcycle 11 tar_pos -32
	setcycle 11 dis_pos -320
	setcycle 11 time 1200
	setcycle 11 dialog ""
	setcycle 11 dialog2 ""
	setcycle 11 y -64
	setcycle 12 correct_response 1
	setcycle 12 shape_target 4
	setcycle 12 shape_distractor 13
	setcycle 12 tar_pos 32
	setcycle 12 dis_pos 320
	setcycle 12 time 1200
	setcycle 12 dialog ""
	setcycle 12 dialog2 ""
	setcycle 12 y 64
	setcycle 13 correct_response 2
	setcycle 13 shape_target 13
	setcycle 13 shape_distractor 1
	setcycle 13 tar_pos 320
	setcycle 13 dis_pos 32
	setcycle 13 time 1200
	setcycle 13 dialog ""
	setcycle 13 dialog2 ""
	setcycle 13 y 64
	setcycle 14 correct_response 1
	setcycle 14 shape_target 1
	setcycle 14 shape_distractor 10
	setcycle 14 tar_pos -320
	setcycle 14 dis_pos -32
	setcycle 14 time 1200
	setcycle 14 dialog ""
	setcycle 14 dialog2 ""
	setcycle 14 y -64
	setcycle 15 correct_response 2
	setcycle 15 shape_target 10
	setcycle 15 shape_distractor 5
	setcycle 15 tar_pos 320
	setcycle 15 dis_pos 32
	setcycle 15 time 1200
	setcycle 15 dialog ""
	setcycle 15 dialog2 ""
	setcycle 15 y 64
	setcycle 16 correct_response 1
	setcycle 16 shape_target 5
	setcycle 16 shape_distractor 9
	setcycle 16 tar_pos -160
	setcycle 16 dis_pos 160
	setcycle 16 time 1200
	setcycle 16 dialog ""
	setcycle 16 dialog2 ""
	setcycle 16 y 0
	setcycle 17 correct_response 2
	setcycle 17 shape_target 9
	setcycle 17 shape_distractor 5
	setcycle 17 tar_pos -32
	setcycle 17 dis_pos -320
	setcycle 17 time 1200
	setcycle 17 dialog ""
	setcycle 17 dialog2 ""
	setcycle 17 y 64
	setcycle 18 correct_response 2
	setcycle 18 shape_target 5
	setcycle 18 shape_distractor 14
	setcycle 18 tar_pos -32
	setcycle 18 dis_pos -320
	setcycle 18 time 1200
	setcycle 18 dialog ""
	setcycle 18 dialog2 ""
	setcycle 18 y -64
	setcycle 19 correct_response 2
	setcycle 19 shape_target 14
	setcycle 19 shape_distractor 3
	setcycle 19 tar_pos 160
	setcycle 19 dis_pos -160
	setcycle 19 time 1200
	setcycle 19 dialog ""
	setcycle 19 dialog2 ""
	setcycle 19 y 0
	setcycle 20 correct_response 1
	setcycle 20 shape_target 3
	setcycle 20 shape_distractor 13
	setcycle 20 tar_pos 32
	setcycle 20 dis_pos 320
	setcycle 20 time 1200
	setcycle 20 dialog ""
	setcycle 20 dialog2 ""
	setcycle 20 y 64
	setcycle 21 correct_response 1
	setcycle 21 shape_target 13
	setcycle 21 shape_distractor 6
	setcycle 21 tar_pos -320
	setcycle 21 dis_pos -32
	setcycle 21 time 1200
	setcycle 21 dialog ""
	setcycle 21 dialog2 ""
	setcycle 21 y -64
	setcycle 22 correct_response 2
	setcycle 22 shape_target 6
	setcycle 22 shape_distractor 14
	setcycle 22 tar_pos -32
	setcycle 22 dis_pos -320
	setcycle 22 time 1200
	setcycle 22 dialog ""
	setcycle 22 dialog2 ""
	setcycle 22 y -64
	setcycle 23 correct_response 1
	setcycle 23 shape_target 14
	setcycle 23 shape_distractor 4
	setcycle 23 tar_pos -320
	setcycle 23 dis_pos -32
	setcycle 23 time 1200
	setcycle 23 dialog ""
	setcycle 23 dialog2 ""
	setcycle 23 y 64
	setcycle 24 correct_response 1
	setcycle 24 shape_target 4
	setcycle 24 shape_distractor 14
	setcycle 24 tar_pos 32
	setcycle 24 dis_pos 320
	setcycle 24 time 1200
	setcycle 24 dialog ""
	setcycle 24 dialog2 ""
	setcycle 24 y -64
	setcycle 25 correct_response 1
	setcycle 25 shape_target 14
	setcycle 25 shape_distractor 1
	setcycle 25 tar_pos 32
	setcycle 25 dis_pos 320
	setcycle 25 time 1200
	setcycle 25 dialog ""
	setcycle 25 dialog2 ""
	setcycle 25 y -64
	setcycle 26 correct_response 2
	setcycle 26 shape_target 1
	setcycle 26 shape_distractor 15
	setcycle 26 tar_pos 320
	setcycle 26 dis_pos 32
	setcycle 26 time 1200
	setcycle 26 dialog ""
	setcycle 26 dialog2 ""
	setcycle 26 y 64
	setcycle 27 correct_response 2
	setcycle 27 shape_target 15
	setcycle 27 shape_distractor 3
	setcycle 27 tar_pos 320
	setcycle 27 dis_pos 32
	setcycle 27 time 1200
	setcycle 27 dialog ""
	setcycle 27 dialog2 ""
	setcycle 27 y 64
	setcycle 28 correct_response 1
	setcycle 28 shape_target 3
	setcycle 28 shape_distractor 12
	setcycle 28 tar_pos -320
	setcycle 28 dis_pos -32
	setcycle 28 time 1200
	setcycle 28 dialog ""
	setcycle 28 dialog2 ""
	setcycle 28 y -64
	setcycle 29 correct_response 2
	setcycle 29 shape_target 12
	setcycle 29 shape_distractor 7
	setcycle 29 tar_pos -32
	setcycle 29 dis_pos -320
	setcycle 29 time 1200
	setcycle 29 dialog ""
	setcycle 29 dialog2 ""
	setcycle 29 y 64
	setcycle 30 correct_response 1
	setcycle 30 shape_target 7
	setcycle 30 shape_distractor 9
	setcycle 30 tar_pos 32
	setcycle 30 dis_pos 320
	setcycle 30 time 1200
	setcycle 30 dialog ""
	setcycle 30 dialog2 ""
	setcycle 30 y -64
	setcycle 31 correct_response 1
	setcycle 31 shape_target 9
	setcycle 31 shape_distractor 3
	setcycle 31 tar_pos 32
	setcycle 31 dis_pos 320
	setcycle 31 time 1200
	setcycle 31 dialog ""
	setcycle 31 dialog2 ""
	setcycle 31 y -64
	setcycle 32 correct_response 2
	setcycle 32 shape_target 3
	setcycle 32 shape_distractor 11
	setcycle 32 tar_pos -32
	setcycle 32 dis_pos -320
	setcycle 32 time 1200
	setcycle 32 dialog ""
	setcycle 32 dialog2 ""
	setcycle 32 y 64
	setcycle 33 correct_response 2
	setcycle 33 shape_target 11
	setcycle 33 shape_distractor 3
	setcycle 33 tar_pos -32
	setcycle 33 dis_pos -320
	setcycle 33 time 1200
	setcycle 33 dialog ""
	setcycle 33 dialog2 ""
	setcycle 33 y 64
	setcycle 34 correct_response 2
	setcycle 34 shape_target 3
	setcycle 34 shape_distractor 8
	setcycle 34 tar_pos -32
	setcycle 34 dis_pos -320
	setcycle 34 time 1200
	setcycle 34 dialog ""
	setcycle 34 dialog2 ""
	setcycle 34 y -64
	setcycle 35 correct_response 1
	setcycle 35 shape_target 8
	setcycle 35 shape_distractor 7
	setcycle 35 tar_pos -320
	setcycle 35 dis_pos -32
	setcycle 35 time 1200
	setcycle 35 dialog ""
	setcycle 35 dialog2 ""
	setcycle 35 y 64
	setcycle 36 correct_response 1
	setcycle 36 shape_target 7
	setcycle 36 shape_distractor 8
	setcycle 36 tar_pos -320
	setcycle 36 dis_pos -32
	setcycle 36 time 1200
	setcycle 36 dialog ""
	setcycle 36 dialog2 ""
	setcycle 36 y 64
	setcycle 37 correct_response 1
	setcycle 37 shape_target 8
	setcycle 37 shape_distractor 2
	setcycle 37 tar_pos -320
	setcycle 37 dis_pos -32
	setcycle 37 time 1200
	setcycle 37 dialog ""
	setcycle 37 dialog2 ""
	setcycle 37 y -64
	setcycle 38 correct_response 2
	setcycle 38 shape_target 2
	setcycle 38 shape_distractor 12
	setcycle 38 tar_pos -32
	setcycle 38 dis_pos -320
	setcycle 38 time 1200
	setcycle 38 dialog ""
	setcycle 38 dialog2 ""
	setcycle 38 y 64
	setcycle 39 correct_response 2
	setcycle 39 shape_target 12
	setcycle 39 shape_distractor 1
	setcycle 39 tar_pos -32
	setcycle 39 dis_pos -320
	setcycle 39 time 1200
	setcycle 39 dialog ""
	setcycle 39 dialog2 ""
	setcycle 39 y 64
	setcycle 40 correct_response 2
	setcycle 40 shape_target 1
	setcycle 40 shape_distractor 15
	setcycle 40 tar_pos 160
	setcycle 40 dis_pos -160
	setcycle 40 time 1200
	setcycle 40 dialog ""
	setcycle 40 dialog2 ""
	setcycle 40 y 0
	setcycle 41 correct_response 2
	setcycle 41 shape_target 15
	setcycle 41 shape_distractor 2
	setcycle 41 tar_pos 320
	setcycle 41 dis_pos 32
	setcycle 41 time 1200
	setcycle 41 dialog ""
	setcycle 41 dialog2 ""
	setcycle 41 y -64
	setcycle 42 correct_response 1
	setcycle 42 shape_target 2
	setcycle 42 shape_distractor 8
	setcycle 42 tar_pos -160
	setcycle 42 dis_pos 160
	setcycle 42 time 1200
	setcycle 42 dialog ""
	setcycle 42 dialog2 ""
	setcycle 42 y 0
	setcycle 43 correct_response 1
	setcycle 43 shape_target 8
	setcycle 43 shape_distractor 6
	setcycle 43 tar_pos 32
	setcycle 43 dis_pos 320
	setcycle 43 time 1200
	setcycle 43 dialog ""
	setcycle 43 dialog2 ""
	setcycle 43 y -64
	setcycle 44 correct_response 2
	setcycle 44 shape_target 6
	setcycle 44 shape_distractor 8
	setcycle 44 tar_pos -32
	setcycle 44 dis_pos -320
	setcycle 44 time 1200
	setcycle 44 dialog ""
	setcycle 44 dialog2 ""
	setcycle 44 y 64
	setcycle 45 correct_response 1
	setcycle 45 shape_target 8
	setcycle 45 shape_distractor 2
	setcycle 45 tar_pos 32
	setcycle 45 dis_pos 320
	setcycle 45 time 1200
	setcycle 45 dialog ""
	setcycle 45 dialog2 ""
	setcycle 45 y -64
	setcycle 46 correct_response 2
	setcycle 46 shape_target 2
	setcycle 46 shape_distractor 11
	setcycle 46 tar_pos 160
	setcycle 46 dis_pos -160
	setcycle 46 time 1200
	setcycle 46 dialog ""
	setcycle 46 dialog2 ""
	setcycle 46 y 0
	setcycle 47 correct_response 2
	setcycle 47 shape_target 11
	setcycle 47 shape_distractor 2
	setcycle 47 tar_pos -32
	setcycle 47 dis_pos -320
	setcycle 47 time 1200
	setcycle 47 dialog ""
	setcycle 47 dialog2 ""
	setcycle 47 y -64
	setcycle 48 correct_response 1
	setcycle 48 shape_target 2
	setcycle 48 shape_distractor 9
	setcycle 48 tar_pos 32
	setcycle 48 dis_pos 320
	setcycle 48 time 1200
	setcycle 48 dialog ""
	setcycle 48 dialog2 ""
	setcycle 48 y -64
	setcycle 49 correct_response 1
	setcycle 49 shape_target 9
	setcycle 49 shape_distractor 11
	setcycle 49 tar_pos 32
	setcycle 49 dis_pos 320
	setcycle 49 time 1200
	setcycle 49 dialog ""
	setcycle 49 dialog2 ""
	setcycle 49 y -64
	setcycle 50 correct_response 1
	setcycle 50 shape_target 1
	setcycle 50 shape_distractor 3
	setcycle 50 tar_pos 32
	setcycle 50 dis_pos 320
	setcycle 50 time 1200
	setcycle 50 dialog ""
	setcycle 50 dialog2 ""
	setcycle 50 y 64
	setcycle 51 correct_response 2
	setcycle 51 shape_target 8
	setcycle 51 shape_distractor 10
	setcycle 51 tar_pos -32
	setcycle 51 dis_pos -320
	setcycle 51 time 1200
	setcycle 51 dialog ""
	setcycle 51 dialog2 ""
	setcycle 51 y -64
	setcycle 52 correct_response 1
	setcycle 52 shape_target 4
	setcycle 52 shape_distractor 6
	setcycle 52 tar_pos -160
	setcycle 52 dis_pos 160
	setcycle 52 time 1200
	setcycle 52 dialog ""
	setcycle 52 dialog2 ""
	setcycle 52 y 0
	setcycle 53 correct_response 2
	setcycle 53 shape_target 6
	setcycle 53 shape_distractor 9
	setcycle 53 tar_pos 160
	setcycle 53 dis_pos -160
	setcycle 53 time 1200
	setcycle 53 dialog ""
	setcycle 53 dialog2 ""
	setcycle 53 y 0
	run seq_time

define loop WM_1_Genap
	set source_file ""
	set source table
	set repeat 1
	set order sequential
	set description "Repeatedly runs another item"
	set cycles 54
	set continuous no
	set break_if_on_first yes
	set break_if never
	setcycle 0 correct_response space
	setcycle 0 shape_target 4
	setcycle 0 shape_distractor 13
	setcycle 0 tar_pos 160
	setcycle 0 dis_pos -160
	setcycle 0 time 50000
	setcycle 0 dialog "Ingat kedua gambar berikut beserta posisinya!"
	setcycle 0 dialog2 "Klik spasi untuk melanjutkan!"
	setcycle 0 y 0
	setcycle 1 correct_response 1
	setcycle 1 shape_target 13
	setcycle 1 shape_distractor 3
	setcycle 1 tar_pos -160
	setcycle 1 dis_pos 160
	setcycle 1 time 50000
	setcycle 1 dialog "Gambar di nomor manakah yang ada pada gambar sebelumnya?"
	setcycle 1 dialog2 "Klik angka 1 atau angka 2 pada keyboard!"
	setcycle 1 y 0
	setcycle 2 correct_response 1
	setcycle 2 shape_target 3
	setcycle 2 shape_distractor 9
	setcycle 2 tar_pos -160
	setcycle 2 dis_pos 160
	setcycle 2 time 50000
	setcycle 2 dialog "Ingat gambar sebelumnya! Gambar di nomor manakah yang ada pada gambar sebelumnya?"
	setcycle 2 dialog2 "Klik angka 1 atau angka 2 pada keyboard!"
	setcycle 2 y 0
	setcycle 3 correct_response 1
	setcycle 3 shape_target 9
	setcycle 3 shape_distractor 7
	setcycle 3 tar_pos -160
	setcycle 3 dis_pos 160
	setcycle 3 time 50000
	setcycle 3 dialog "Sudah mengerti cara mainnya? Setelah ini anda harus menjawab dengan cepat!"
	setcycle 3 dialog2 "Klik angka 1 atau angka 2 pada keyboard!"
	setcycle 3 y 0
	setcycle 4 correct_response 2
	setcycle 4 shape_target 7
	setcycle 4 shape_distractor 13
	setcycle 4 tar_pos 160
	setcycle 4 dis_pos -160
	setcycle 4 time 1200
	setcycle 4 dialog ""
	setcycle 4 dialog2 ""
	setcycle 4 y 0
	setcycle 5 correct_response 2
	setcycle 5 shape_target 13
	setcycle 5 shape_distractor 5
	setcycle 5 tar_pos 320
	setcycle 5 dis_pos 32
	setcycle 5 time 1200
	setcycle 5 dialog ""
	setcycle 5 dialog2 ""
	setcycle 5 y 64
	setcycle 6 correct_response 1
	setcycle 6 shape_target 5
	setcycle 6 shape_distractor 13
	setcycle 6 tar_pos -320
	setcycle 6 dis_pos -32
	setcycle 6 time 1200
	setcycle 6 dialog ""
	setcycle 6 dialog2 ""
	setcycle 6 y 64
	setcycle 7 correct_response 2
	setcycle 7 shape_target 13
	setcycle 7 shape_distractor 4
	setcycle 7 tar_pos -32
	setcycle 7 dis_pos -320
	setcycle 7 time 1200
	setcycle 7 dialog ""
	setcycle 7 dialog2 ""
	setcycle 7 y -64
	setcycle 8 correct_response 1
	setcycle 8 shape_target 4
	setcycle 8 shape_distractor 8
	setcycle 8 tar_pos 32
	setcycle 8 dis_pos 320
	setcycle 8 time 1200
	setcycle 8 dialog ""
	setcycle 8 dialog2 ""
	setcycle 8 y -64
	setcycle 9 correct_response 2
	setcycle 9 shape_target 8
	setcycle 9 shape_distractor 6
	setcycle 9 tar_pos 320
	setcycle 9 dis_pos 32
	setcycle 9 time 1200
	setcycle 9 dialog ""
	setcycle 9 dialog2 ""
	setcycle 9 y 64
	setcycle 10 correct_response 1
	setcycle 10 shape_target 6
	setcycle 10 shape_distractor 14
	setcycle 10 tar_pos -320
	setcycle 10 dis_pos -32
	setcycle 10 time 1200
	setcycle 10 dialog ""
	setcycle 10 dialog2 ""
	setcycle 10 y 64
	setcycle 11 correct_response 1
	setcycle 11 shape_target 14
	setcycle 11 shape_distractor 6
	setcycle 11 tar_pos -320
	setcycle 11 dis_pos -32
	setcycle 11 time 1200
	setcycle 11 dialog ""
	setcycle 11 dialog2 ""
	setcycle 11 y -64
	setcycle 12 correct_response 2
	setcycle 12 shape_target 6
	setcycle 12 shape_distractor 10
	setcycle 12 tar_pos 320
	setcycle 12 dis_pos 32
	setcycle 12 time 1200
	setcycle 12 dialog ""
	setcycle 12 dialog2 ""
	setcycle 12 y 64
	setcycle 13 correct_response 1
	setcycle 13 shape_target 10
	setcycle 13 shape_distractor 1
	setcycle 13 tar_pos 32
	setcycle 13 dis_pos 320
	setcycle 13 time 1200
	setcycle 13 dialog ""
	setcycle 13 dialog2 ""
	setcycle 13 y -64
	setcycle 14 correct_response 1
	setcycle 14 shape_target 1
	setcycle 14 shape_distractor 13
	setcycle 14 tar_pos 32
	setcycle 14 dis_pos 320
	setcycle 14 time 1200
	setcycle 14 dialog ""
	setcycle 14 dialog2 ""
	setcycle 14 y 64
	setcycle 15 correct_response 1
	setcycle 15 shape_target 13
	setcycle 15 shape_distractor 6
	setcycle 15 tar_pos 32
	setcycle 15 dis_pos 320
	setcycle 15 time 1200
	setcycle 15 dialog ""
	setcycle 15 dialog2 ""
	setcycle 15 y -64
	setcycle 16 correct_response 2
	setcycle 16 shape_target 6
	setcycle 16 shape_distractor 11
	setcycle 16 tar_pos 160
	setcycle 16 dis_pos -160
	setcycle 16 time 1200
	setcycle 16 dialog ""
	setcycle 16 dialog2 ""
	setcycle 16 y 0
	setcycle 17 correct_response 1
	setcycle 17 shape_target 11
	setcycle 17 shape_distractor 4
	setcycle 17 tar_pos 32
	setcycle 17 dis_pos 320
	setcycle 17 time 1200
	setcycle 17 dialog ""
	setcycle 17 dialog2 ""
	setcycle 17 y 64
	setcycle 18 correct_response 1
	setcycle 18 shape_target 4
	setcycle 18 shape_distractor 14
	setcycle 18 tar_pos 32
	setcycle 18 dis_pos 320
	setcycle 18 time 1200
	setcycle 18 dialog ""
	setcycle 18 dialog2 ""
	setcycle 18 y 64
	setcycle 19 correct_response 2
	setcycle 19 shape_target 14
	setcycle 19 shape_distractor 6
	setcycle 19 tar_pos 160
	setcycle 19 dis_pos -160
	setcycle 19 time 1200
	setcycle 19 dialog ""
	setcycle 19 dialog2 ""
	setcycle 19 y 0
	setcycle 20 correct_response 2
	setcycle 20 shape_target 6
	setcycle 20 shape_distractor 10
	setcycle 20 tar_pos 320
	setcycle 20 dis_pos 32
	setcycle 20 time 1200
	setcycle 20 dialog ""
	setcycle 20 dialog2 ""
	setcycle 20 y 64
	setcycle 21 correct_response 2
	setcycle 21 shape_target 10
	setcycle 21 shape_distractor 2
	setcycle 21 tar_pos 320
	setcycle 21 dis_pos 32
	setcycle 21 time 1200
	setcycle 21 dialog ""
	setcycle 21 dialog2 ""
	setcycle 21 y 64
	setcycle 22 correct_response 1
	setcycle 22 shape_target 2
	setcycle 22 shape_distractor 13
	setcycle 22 tar_pos -160
	setcycle 22 dis_pos 160
	setcycle 22 time 1200
	setcycle 22 dialog ""
	setcycle 22 dialog2 ""
	setcycle 22 y 0
	setcycle 23 correct_response 1
	setcycle 23 shape_target 13
	setcycle 23 shape_distractor 2
	setcycle 23 tar_pos 32
	setcycle 23 dis_pos 320
	setcycle 23 time 1200
	setcycle 23 dialog ""
	setcycle 23 dialog2 ""
	setcycle 23 y -64
	setcycle 24 correct_response 1
	setcycle 24 shape_target 2
	setcycle 24 shape_distractor 8
	setcycle 24 tar_pos 32
	setcycle 24 dis_pos 320
	setcycle 24 time 1200
	setcycle 24 dialog ""
	setcycle 24 dialog2 ""
	setcycle 24 y 64
	setcycle 25 correct_response 2
	setcycle 25 shape_target 8
	setcycle 25 shape_distractor 4
	setcycle 25 tar_pos -32
	setcycle 25 dis_pos -320
	setcycle 25 time 1200
	setcycle 25 dialog ""
	setcycle 25 dialog2 ""
	setcycle 25 y -64
	setcycle 26 correct_response 1
	setcycle 26 shape_target 4
	setcycle 26 shape_distractor 8
	setcycle 26 tar_pos 32
	setcycle 26 dis_pos 320
	setcycle 26 time 1200
	setcycle 26 dialog ""
	setcycle 26 dialog2 ""
	setcycle 26 y -64
	setcycle 27 correct_response 2
	setcycle 27 shape_target 8
	setcycle 27 shape_distractor 3
	setcycle 27 tar_pos 320
	setcycle 27 dis_pos 32
	setcycle 27 time 1200
	setcycle 27 dialog ""
	setcycle 27 dialog2 ""
	setcycle 27 y 64
	setcycle 28 correct_response 2
	setcycle 28 shape_target 3
	setcycle 28 shape_distractor 12
	setcycle 28 tar_pos 320
	setcycle 28 dis_pos 32
	setcycle 28 time 1200
	setcycle 28 dialog ""
	setcycle 28 dialog2 ""
	setcycle 28 y -64
	setcycle 29 correct_response 1
	setcycle 29 shape_target 12
	setcycle 29 shape_distractor 3
	setcycle 29 tar_pos -160
	setcycle 29 dis_pos 160
	setcycle 29 time 1200
	setcycle 29 dialog ""
	setcycle 29 dialog2 ""
	setcycle 29 y 0
	setcycle 30 correct_response 1
	setcycle 30 shape_target 3
	setcycle 30 shape_distractor 10
	setcycle 30 tar_pos -320
	setcycle 30 dis_pos -32
	setcycle 30 time 1200
	setcycle 30 dialog ""
	setcycle 30 dialog2 ""
	setcycle 30 y -64
	setcycle 31 correct_response 2
	setcycle 31 shape_target 10
	setcycle 31 shape_distractor 5
	setcycle 31 tar_pos 160
	setcycle 31 dis_pos -160
	setcycle 31 time 1200
	setcycle 31 dialog ""
	setcycle 31 dialog2 ""
	setcycle 31 y 0
	setcycle 32 correct_response 1
	setcycle 32 shape_target 5
	setcycle 32 shape_distractor 12
	setcycle 32 tar_pos 32
	setcycle 32 dis_pos 320
	setcycle 32 time 1200
	setcycle 32 dialog ""
	setcycle 32 dialog2 ""
	setcycle 32 y 64
	setcycle 33 correct_response 1
	setcycle 33 shape_target 12
	setcycle 33 shape_distractor 7
	setcycle 33 tar_pos -160
	setcycle 33 dis_pos 160
	setcycle 33 time 1200
	setcycle 33 dialog ""
	setcycle 33 dialog2 ""
	setcycle 33 y 0
	setcycle 34 correct_response 2
	setcycle 34 shape_target 7
	setcycle 34 shape_distractor 12
	setcycle 34 tar_pos 320
	setcycle 34 dis_pos 32
	setcycle 34 time 1200
	setcycle 34 dialog ""
	setcycle 34 dialog2 ""
	setcycle 34 y 64
	setcycle 35 correct_response 2
	setcycle 35 shape_target 12
	setcycle 35 shape_distractor 6
	setcycle 35 tar_pos 320
	setcycle 35 dis_pos 32
	setcycle 35 time 1200
	setcycle 35 dialog ""
	setcycle 35 dialog2 ""
	setcycle 35 y -64
	setcycle 36 correct_response 2
	setcycle 36 shape_target 6
	setcycle 36 shape_distractor 15
	setcycle 36 tar_pos 320
	setcycle 36 dis_pos 32
	setcycle 36 time 1200
	setcycle 36 dialog ""
	setcycle 36 dialog2 ""
	setcycle 36 y -64
	setcycle 37 correct_response 1
	setcycle 37 shape_target 15
	setcycle 37 shape_distractor 1
	setcycle 37 tar_pos 32
	setcycle 37 dis_pos 320
	setcycle 37 time 1200
	setcycle 37 dialog ""
	setcycle 37 dialog2 ""
	setcycle 37 y -64
	setcycle 38 correct_response 2
	setcycle 38 shape_target 1
	setcycle 38 shape_distractor 8
	setcycle 38 tar_pos 160
	setcycle 38 dis_pos -160
	setcycle 38 time 1200
	setcycle 38 dialog ""
	setcycle 38 dialog2 ""
	setcycle 38 y 0
	setcycle 39 correct_response 1
	setcycle 39 shape_target 8
	setcycle 39 shape_distractor 2
	setcycle 39 tar_pos -320
	setcycle 39 dis_pos -32
	setcycle 39 time 1200
	setcycle 39 dialog ""
	setcycle 39 dialog2 ""
	setcycle 39 y 64
	setcycle 40 correct_response 1
	setcycle 40 shape_target 2
	setcycle 40 shape_distractor 13
	setcycle 40 tar_pos 32
	setcycle 40 dis_pos 320
	setcycle 40 time 1200
	setcycle 40 dialog ""
	setcycle 40 dialog2 ""
	setcycle 40 y -64
	setcycle 41 correct_response 1
	setcycle 41 shape_target 13
	setcycle 41 shape_distractor 4
	setcycle 41 tar_pos -160
	setcycle 41 dis_pos 160
	setcycle 41 time 1200
	setcycle 41 dialog ""
	setcycle 41 dialog2 ""
	setcycle 41 y 0
	setcycle 42 correct_response 1
	setcycle 42 shape_target 4
	setcycle 42 shape_distractor 13
	setcycle 42 tar_pos -320
	setcycle 42 dis_pos -32
	setcycle 42 time 1200
	setcycle 42 dialog ""
	setcycle 42 dialog2 ""
	setcycle 42 y -64
	setcycle 43 correct_response 2
	setcycle 43 shape_target 13
	setcycle 43 shape_distractor 1
	setcycle 43 tar_pos 320
	setcycle 43 dis_pos 32
	setcycle 43 time 1200
	setcycle 43 dialog ""
	setcycle 43 dialog2 ""
	setcycle 43 y 64
	setcycle 44 correct_response 1
	setcycle 44 shape_target 1
	setcycle 44 shape_distractor 10
	setcycle 44 tar_pos 32
	setcycle 44 dis_pos 320
	setcycle 44 time 1200
	setcycle 44 dialog ""
	setcycle 44 dialog2 ""
	setcycle 44 y -64
	setcycle 45 correct_response 2
	setcycle 45 shape_target 10
	setcycle 45 shape_distractor 3
	setcycle 45 tar_pos -32
	setcycle 45 dis_pos -320
	setcycle 45 time 1200
	setcycle 45 dialog ""
	setcycle 45 dialog2 ""
	setcycle 45 y -64
	setcycle 46 correct_response 2
	setcycle 46 shape_target 3
	setcycle 46 shape_distractor 9
	setcycle 46 tar_pos 320
	setcycle 46 dis_pos 32
	setcycle 46 time 1200
	setcycle 46 dialog ""
	setcycle 46 dialog2 ""
	setcycle 46 y 64
	setcycle 47 correct_response 1
	setcycle 47 shape_target 9
	setcycle 47 shape_distractor 1
	setcycle 47 tar_pos -320
	setcycle 47 dis_pos -32
	setcycle 47 time 1200
	setcycle 47 dialog ""
	setcycle 47 dialog2 ""
	setcycle 47 y -64
	setcycle 48 correct_response 2
	setcycle 48 shape_target 1
	setcycle 48 shape_distractor 14
	setcycle 48 tar_pos 320
	setcycle 48 dis_pos 32
	setcycle 48 time 1200
	setcycle 48 dialog ""
	setcycle 48 dialog2 ""
	setcycle 48 y 64
	setcycle 49 correct_response 1
	setcycle 49 shape_target 14
	setcycle 49 shape_distractor 16
	setcycle 49 tar_pos -320
	setcycle 49 dis_pos -32
	setcycle 49 time 1200
	setcycle 49 dialog ""
	setcycle 49 dialog2 ""
	setcycle 49 y -64
	setcycle 50 correct_response 1
	setcycle 50 shape_target 5
	setcycle 50 shape_distractor 7
	setcycle 50 tar_pos -320
	setcycle 50 dis_pos -32
	setcycle 50 time 1200
	setcycle 50 dialog ""
	setcycle 50 dialog2 ""
	setcycle 50 y 64
	setcycle 51 correct_response 1
	setcycle 51 shape_target 8
	setcycle 51 shape_distractor 10
	setcycle 51 tar_pos 32
	setcycle 51 dis_pos 320
	setcycle 51 time 1200
	setcycle 51 dialog ""
	setcycle 51 dialog2 ""
	setcycle 51 y -64
	setcycle 52 correct_response 2
	setcycle 52 shape_target 5
	setcycle 52 shape_distractor 7
	setcycle 52 tar_pos -32
	setcycle 52 dis_pos -320
	setcycle 52 time 1200
	setcycle 52 dialog ""
	setcycle 52 dialog2 ""
	setcycle 52 y 64
	setcycle 53 correct_response 2
	setcycle 53 shape_target 5
	setcycle 53 shape_distractor 10
	setcycle 53 tar_pos 160
	setcycle 53 dis_pos -160
	setcycle 53 time 1200
	setcycle 53 dialog ""
	setcycle 53 dialog2 ""
	setcycle 53 y 0
	run seq_time

define loop WM_2
	set source_file ""
	set source table
	set repeat 1
	set order random
	set description "Repeatedly runs another item"
	set cycles 1
	set continuous no
	set break_if_on_first yes
	set break_if never
	setcycle 0 test_session energy_test
	run SEQ_2

define loop WM_2_Ganjil
	set source_file ""
	set source table
	set repeat 1
	set order sequential
	set description "Repeatedly runs another item"
	set cycles 54
	set continuous no
	set break_if_on_first yes
	set break_if never
	setcycle 0 stim B3
	setcycle 0 correct_response space
	setcycle 0 time 50000
	setcycle 0 dialog "Ingat jumlah titik pada kartu diatas!"
	setcycle 0 dialog2 "Klik spasi!"
	setcycle 1 stim B33
	setcycle 1 correct_response 6
	setcycle 1 time 50000
	setcycle 1 dialog "Jumlahkan titik kartu ini"
	setcycle 1 dialog2 "dengan jumlah titik angka pada kartu sebelumnya!"
	setcycle 2 stim B0
	setcycle 2 correct_response 3
	setcycle 2 time 50000
	setcycle 2 dialog "Jumlahkan kartu sebelumnya dengan kartu yang ini..."
	setcycle 2 dialog2 ""
	setcycle 3 stim B6
	setcycle 3 correct_response 6
	setcycle 3 time 50000
	setcycle 3 dialog "Jumlahkan kartu sebelumnya dengan kartu yang ini..."
	setcycle 3 dialog2 ""
	setcycle 4 stim B1
	setcycle 4 correct_response 7
	setcycle 4 time 50000
	setcycle 4 dialog "Anda mengerti?"
	setcycle 4 dialog2 "Lanjutkan penjumlahan.."
	setcycle 5 stim B1
	setcycle 5 correct_response 2
	setcycle 5 time 50000
	setcycle 5 dialog ""
	setcycle 5 dialog2 ""
	setcycle 6 stim B4
	setcycle 6 correct_response 5
	setcycle 6 time 50000
	setcycle 6 dialog ""
	setcycle 6 dialog2 ""
	setcycle 7 stim B44
	setcycle 7 correct_response 8
	setcycle 7 time 50000
	setcycle 7 dialog ""
	setcycle 7 dialog2 ""
	setcycle 8 stim B3
	setcycle 8 correct_response 7
	setcycle 8 time 50000
	setcycle 8 dialog ""
	setcycle 8 dialog2 ""
	setcycle 9 stim B33
	setcycle 9 correct_response 6
	setcycle 9 time 50000
	setcycle 9 dialog ""
	setcycle 9 dialog2 ""
	setcycle 10 stim B0
	setcycle 10 correct_response 3
	setcycle 10 time 50000
	setcycle 10 dialog ""
	setcycle 10 dialog2 ""
	setcycle 11 stim B2
	setcycle 11 correct_response 2
	setcycle 11 time 50000
	setcycle 11 dialog ""
	setcycle 11 dialog2 ""
	setcycle 12 stim B33
	setcycle 12 correct_response 5
	setcycle 12 time 50000
	setcycle 12 dialog ""
	setcycle 12 dialog2 ""
	setcycle 13 stim B3
	setcycle 13 correct_response 6
	setcycle 13 time 50000
	setcycle 13 dialog ""
	setcycle 13 dialog2 ""
	setcycle 14 stim B2
	setcycle 14 correct_response 5
	setcycle 14 time 50000
	setcycle 14 dialog ""
	setcycle 14 dialog2 ""
	setcycle 15 stim B55
	setcycle 15 correct_response 7
	setcycle 15 time 50000
	setcycle 15 dialog ""
	setcycle 15 dialog2 ""
	setcycle 16 stim B444
	setcycle 16 correct_response 9
	setcycle 16 time 50000
	setcycle 16 dialog ""
	setcycle 16 dialog2 ""
	setcycle 17 stim B4
	setcycle 17 correct_response 8
	setcycle 17 time 50000
	setcycle 17 dialog ""
	setcycle 17 dialog2 ""
	setcycle 18 stim B1
	setcycle 18 correct_response 5
	setcycle 18 time 50000
	setcycle 18 dialog ""
	setcycle 18 dialog2 ""
	setcycle 19 stim B1
	setcycle 19 correct_response 2
	setcycle 19 time 50000
	setcycle 19 dialog ""
	setcycle 19 dialog2 ""
	setcycle 20 stim B0
	setcycle 20 correct_response 1
	setcycle 20 time 50000
	setcycle 20 dialog ""
	setcycle 20 dialog2 ""
	setcycle 21 stim B0
	setcycle 21 correct_response 0
	setcycle 21 time 50000
	setcycle 21 dialog ""
	setcycle 21 dialog2 ""
	setcycle 22 stim B4
	setcycle 22 correct_response 4
	setcycle 22 time 50000
	setcycle 22 dialog ""
	setcycle 22 dialog2 ""
	setcycle 23 stim B3
	setcycle 23 correct_response 7
	setcycle 23 time 50000
	setcycle 23 dialog ""
	setcycle 23 dialog2 ""
	setcycle 24 stim B33
	setcycle 24 correct_response 6
	setcycle 24 time 50000
	setcycle 24 dialog ""
	setcycle 24 dialog2 ""
	setcycle 25 stim B3
	setcycle 25 correct_response 6
	setcycle 25 time 50000
	setcycle 25 dialog ""
	setcycle 25 dialog2 ""
	setcycle 26 stim B33
	setcycle 26 correct_response 6
	setcycle 26 time 50000
	setcycle 26 dialog ""
	setcycle 26 dialog2 ""
	setcycle 27 stim B2
	setcycle 27 correct_response 5
	setcycle 27 time 50000
	setcycle 27 dialog ""
	setcycle 27 dialog2 ""
	setcycle 28 stim B5
	setcycle 28 correct_response 7
	setcycle 28 time 50000
	setcycle 28 dialog ""
	setcycle 28 dialog2 ""
	setcycle 29 stim B1
	setcycle 29 correct_response 6
	setcycle 29 time 50000
	setcycle 29 dialog ""
	setcycle 29 dialog2 ""
	setcycle 30 stim B1
	setcycle 30 correct_response 2
	setcycle 30 time 50000
	setcycle 30 dialog ""
	setcycle 30 dialog2 ""
	setcycle 31 stim B0
	setcycle 31 correct_response 1
	setcycle 31 time 50000
	setcycle 31 dialog ""
	setcycle 31 dialog2 ""
	setcycle 32 stim B10
	setcycle 32 correct_response 0
	setcycle 32 time 50000
	setcycle 32 dialog "Jika angkanya belasan atau puluhan, jawab dengan ketik angka akhirnya saja!"
	setcycle 32 dialog2 "Ketik angka ujungnya"
	setcycle 33 stim B0
	setcycle 33 correct_response 0
	setcycle 33 time 50000
	setcycle 33 dialog ""
	setcycle 33 dialog2 ""
	setcycle 34 stim B2
	setcycle 34 correct_response 2
	setcycle 34 time 50000
	setcycle 34 dialog ""
	setcycle 34 dialog2 ""
	setcycle 35 stim B3
	setcycle 35 correct_response 5
	setcycle 35 time 50000
	setcycle 35 dialog ""
	setcycle 35 dialog2 ""
	setcycle 36 stim B4
	setcycle 36 correct_response 7
	setcycle 36 time 50000
	setcycle 36 dialog ""
	setcycle 36 dialog2 ""
	setcycle 37 stim B666
	setcycle 37 correct_response 0
	setcycle 37 time 50000
	setcycle 37 dialog ""
	setcycle 37 dialog2 ""
	setcycle 38 stim B7
	setcycle 38 correct_response 3
	setcycle 38 time 50000
	setcycle 38 dialog ""
	setcycle 38 dialog2 ""
	setcycle 39 stim B4
	setcycle 39 correct_response 1
	setcycle 39 time 50000
	setcycle 39 dialog ""
	setcycle 39 dialog2 ""
	setcycle 40 stim B77
	setcycle 40 correct_response 1
	setcycle 40 time 50000
	setcycle 40 dialog ""
	setcycle 40 dialog2 ""
	setcycle 41 stim B0
	setcycle 41 correct_response 7
	setcycle 41 time 50000
	setcycle 41 dialog ""
	setcycle 41 dialog2 ""
	setcycle 42 stim B8
	setcycle 42 correct_response 8
	setcycle 42 time 50000
	setcycle 42 dialog ""
	setcycle 42 dialog2 ""
	setcycle 43 stim B2
	setcycle 43 correct_response 0
	setcycle 43 time 50000
	setcycle 43 dialog ""
	setcycle 43 dialog2 ""
	setcycle 44 stim B4
	setcycle 44 correct_response 6
	setcycle 44 time 50000
	setcycle 44 dialog ""
	setcycle 44 dialog2 ""
	setcycle 45 stim B444
	setcycle 45 correct_response 8
	setcycle 45 time 50000
	setcycle 45 dialog ""
	setcycle 45 dialog2 ""
	setcycle 46 stim B8
	setcycle 46 correct_response 2
	setcycle 46 time 50000
	setcycle 46 dialog ""
	setcycle 46 dialog2 ""
	setcycle 47 stim B1
	setcycle 47 correct_response 9
	setcycle 47 time 50000
	setcycle 47 dialog ""
	setcycle 47 dialog2 ""
	setcycle 48 stim B3
	setcycle 48 correct_response 4
	setcycle 48 time 50000
	setcycle 48 dialog ""
	setcycle 48 dialog2 ""
	setcycle 49 stim B0
	setcycle 49 correct_response 3
	setcycle 49 time 50000
	setcycle 49 dialog ""
	setcycle 49 dialog2 ""
	setcycle 50 stim B5
	setcycle 50 correct_response 5
	setcycle 50 time 50000
	setcycle 50 dialog ""
	setcycle 50 dialog2 ""
	setcycle 51 stim B1
	setcycle 51 correct_response 6
	setcycle 51 time 50000
	setcycle 51 dialog ""
	setcycle 51 dialog2 ""
	setcycle 52 stim B8
	setcycle 52 correct_response 9
	setcycle 52 time 50000
	setcycle 52 dialog ""
	setcycle 52 dialog2 ""
	setcycle 53 stim B1
	setcycle 53 correct_response 9
	setcycle 53 time 50000
	setcycle 53 dialog ""
	setcycle 53 dialog2 ""
	run seq_energy

define loop WM_2_Genap
	set source_file ""
	set source table
	set repeat 1
	set order sequential
	set description "Repeatedly runs another item"
	set cycles 54
	set continuous no
	set break_if_on_first yes
	set break_if never
	setcycle 0 stim B5
	setcycle 0 correct_response space
	setcycle 0 time 50000
	setcycle 0 dialog "Ingat jumlah titik pada kartu diatas!"
	setcycle 0 dialog2 "Klik spasi!"
	setcycle 1 stim B1
	setcycle 1 correct_response 6
	setcycle 1 time 50000
	setcycle 1 dialog "Jumlahkan titik kartu ini"
	setcycle 1 dialog2 "dengan jumlah titik angka pada kartu sebelumnya!"
	setcycle 2 stim B4
	setcycle 2 correct_response 5
	setcycle 2 time 50000
	setcycle 2 dialog "Jumlahkan kartu sebelumnya dengan kartu yang ini..."
	setcycle 2 dialog2 ""
	setcycle 3 stim B4
	setcycle 3 correct_response 8
	setcycle 3 time 50000
	setcycle 3 dialog "Jumlahkan kartu sebelumnya dengan kartu yang ini..."
	setcycle 3 dialog2 ""
	setcycle 4 stim B3
	setcycle 4 correct_response 7
	setcycle 4 time 50000
	setcycle 4 dialog "Anda mengerti?"
	setcycle 4 dialog2 "Lanjutkan penjumlahan.."
	setcycle 5 stim B4
	setcycle 5 correct_response 7
	setcycle 5 time 50000
	setcycle 5 dialog ""
	setcycle 5 dialog2 ""
	setcycle 6 stim B1
	setcycle 6 correct_response 5
	setcycle 6 time 50000
	setcycle 6 dialog ""
	setcycle 6 dialog2 ""
	setcycle 7 stim B3
	setcycle 7 correct_response 4
	setcycle 7 time 50000
	setcycle 7 dialog ""
	setcycle 7 dialog2 ""
	setcycle 8 stim B4
	setcycle 8 correct_response 7
	setcycle 8 time 50000
	setcycle 8 dialog ""
	setcycle 8 dialog2 ""
	setcycle 9 stim B0
	setcycle 9 correct_response 4
	setcycle 9 time 50000
	setcycle 9 dialog ""
	setcycle 9 dialog2 ""
	setcycle 10 stim B5
	setcycle 10 correct_response 5
	setcycle 10 time 50000
	setcycle 10 dialog ""
	setcycle 10 dialog2 ""
	setcycle 11 stim B0
	setcycle 11 correct_response 5
	setcycle 11 time 50000
	setcycle 11 dialog ""
	setcycle 11 dialog2 ""
	setcycle 12 stim B33
	setcycle 12 correct_response 3
	setcycle 12 time 50000
	setcycle 12 dialog ""
	setcycle 12 dialog2 ""
	setcycle 13 stim B3
	setcycle 13 correct_response 6
	setcycle 13 time 50000
	setcycle 13 dialog ""
	setcycle 13 dialog2 ""
	setcycle 14 stim B9
	setcycle 14 correct_response 2
	setcycle 14 time 50000
	setcycle 14 dialog "Jika angkanya belasan atau puluhan, jawab dengan ketik angka akhirnya saja!"
	setcycle 14 dialog2 "Ketik angka ujungnya"
	setcycle 15 stim B66
	setcycle 15 correct_response 5
	setcycle 15 time 50000
	setcycle 15 dialog ""
	setcycle 15 dialog2 ""
	setcycle 16 stim B0
	setcycle 16 correct_response 6
	setcycle 16 time 50000
	setcycle 16 dialog ""
	setcycle 16 dialog2 ""
	setcycle 17 stim B1
	setcycle 17 correct_response 1
	setcycle 17 time 50000
	setcycle 17 dialog ""
	setcycle 17 dialog2 ""
	setcycle 18 stim B4
	setcycle 18 correct_response 5
	setcycle 18 time 50000
	setcycle 18 dialog ""
	setcycle 18 dialog2 ""
	setcycle 19 stim B22
	setcycle 19 correct_response 6
	setcycle 19 time 50000
	setcycle 19 dialog ""
	setcycle 19 dialog2 ""
	setcycle 20 stim B44
	setcycle 20 correct_response 6
	setcycle 20 time 50000
	setcycle 20 dialog ""
	setcycle 20 dialog2 ""
	setcycle 21 stim B77
	setcycle 21 correct_response 1
	setcycle 21 time 50000
	setcycle 21 dialog ""
	setcycle 21 dialog2 ""
	setcycle 22 stim B22
	setcycle 22 correct_response 9
	setcycle 22 time 50000
	setcycle 22 dialog ""
	setcycle 22 dialog2 ""
	setcycle 23 stim B99
	setcycle 23 correct_response 1
	setcycle 23 time 50000
	setcycle 23 dialog ""
	setcycle 23 dialog2 ""
	setcycle 24 stim B0
	setcycle 24 correct_response 9
	setcycle 24 time 50000
	setcycle 24 dialog ""
	setcycle 24 dialog2 ""
	setcycle 25 stim B9
	setcycle 25 correct_response 9
	setcycle 25 time 50000
	setcycle 25 dialog ""
	setcycle 25 dialog2 ""
	setcycle 26 stim B888
	setcycle 26 correct_response 7
	setcycle 26 time 50000
	setcycle 26 dialog ""
	setcycle 26 dialog2 ""
	setcycle 27 stim B2
	setcycle 27 correct_response 0
	setcycle 27 time 50000
	setcycle 27 dialog ""
	setcycle 27 dialog2 ""
	setcycle 28 stim B777
	setcycle 28 correct_response 9
	setcycle 28 time 50000
	setcycle 28 dialog ""
	setcycle 28 dialog2 ""
	setcycle 29 stim B444
	setcycle 29 correct_response 1
	setcycle 29 time 50000
	setcycle 29 dialog ""
	setcycle 29 dialog2 ""
	setcycle 30 stim B1
	setcycle 30 correct_response 5
	setcycle 30 time 50000
	setcycle 30 dialog ""
	setcycle 30 dialog2 ""
	setcycle 31 stim B555
	setcycle 31 correct_response 6
	setcycle 31 time 50000
	setcycle 31 dialog ""
	setcycle 31 dialog2 ""
	setcycle 32 stim B0
	setcycle 32 correct_response 5
	setcycle 32 time 50000
	setcycle 32 dialog ""
	setcycle 32 dialog2 ""
	setcycle 33 stim B0
	setcycle 33 correct_response 0
	setcycle 33 time 50000
	setcycle 33 dialog ""
	setcycle 33 dialog2 ""
	setcycle 34 stim B33
	setcycle 34 correct_response 3
	setcycle 34 time 50000
	setcycle 34 dialog ""
	setcycle 34 dialog2 ""
	setcycle 35 stim B0
	setcycle 35 correct_response 3
	setcycle 35 time 50000
	setcycle 35 dialog ""
	setcycle 35 dialog2 ""
	setcycle 36 stim B88
	setcycle 36 correct_response 8
	setcycle 36 time 50000
	setcycle 36 dialog ""
	setcycle 36 dialog2 ""
	setcycle 37 stim B7
	setcycle 37 correct_response 5
	setcycle 37 time 50000
	setcycle 37 dialog ""
	setcycle 37 dialog2 ""
	setcycle 38 stim B77
	setcycle 38 correct_response 4
	setcycle 38 time 50000
	setcycle 38 dialog ""
	setcycle 38 dialog2 ""
	setcycle 39 stim B888
	setcycle 39 correct_response 5
	setcycle 39 time 50000
	setcycle 39 dialog ""
	setcycle 39 dialog2 ""
	setcycle 40 stim B33
	setcycle 40 correct_response 1
	setcycle 40 time 50000
	setcycle 40 dialog ""
	setcycle 40 dialog2 ""
	setcycle 41 stim B55
	setcycle 41 correct_response 8
	setcycle 41 time 50000
	setcycle 41 dialog ""
	setcycle 41 dialog2 ""
	setcycle 42 stim B1
	setcycle 42 correct_response 6
	setcycle 42 time 50000
	setcycle 42 dialog ""
	setcycle 42 dialog2 ""
	setcycle 43 stim B444
	setcycle 43 correct_response 5
	setcycle 43 time 50000
	setcycle 43 dialog ""
	setcycle 43 dialog2 ""
	setcycle 44 stim B1
	setcycle 44 correct_response 5
	setcycle 44 time 50000
	setcycle 44 dialog ""
	setcycle 44 dialog2 ""
	setcycle 45 stim B5
	setcycle 45 correct_response 6
	setcycle 45 time 50000
	setcycle 45 dialog ""
	setcycle 45 dialog2 ""
	setcycle 46 stim B1
	setcycle 46 correct_response 6
	setcycle 46 time 50000
	setcycle 46 dialog ""
	setcycle 46 dialog2 ""
	setcycle 47 stim B55
	setcycle 47 correct_response 6
	setcycle 47 time 50000
	setcycle 47 dialog ""
	setcycle 47 dialog2 ""
	setcycle 48 stim B6666
	setcycle 48 correct_response 1
	setcycle 48 time 50000
	setcycle 48 dialog ""
	setcycle 48 dialog2 ""
	setcycle 49 stim B0
	setcycle 49 correct_response 6
	setcycle 49 time 50000
	setcycle 49 dialog ""
	setcycle 49 dialog2 ""
	setcycle 50 stim B22
	setcycle 50 correct_response 2
	setcycle 50 time 50000
	setcycle 50 dialog ""
	setcycle 50 dialog2 ""
	setcycle 51 stim B77
	setcycle 51 correct_response 9
	setcycle 51 time 50000
	setcycle 51 dialog ""
	setcycle 51 dialog2 ""
	setcycle 52 stim B44
	setcycle 52 correct_response 1
	setcycle 52 time 50000
	setcycle 52 dialog ""
	setcycle 52 dialog2 ""
	setcycle 53 stim B555
	setcycle 53 correct_response 9
	setcycle 53 time 50000
	setcycle 53 dialog ""
	setcycle 53 dialog2 ""
	run seq_energy

define loop WM_3
	set source_file ""
	set source table
	set repeat 1
	set order sequential
	set description "Repeatedly runs another item"
	set cycles 1
	set continuous no
	set break_if_on_first yes
	set break_if never
	setcycle 0 test_session capacity_test
	run SEQ_3

define loop WM_3_Ganjil
	set source_file ""
	set source table
	set repeat 1
	set order sequential
	set description "Repeatedly runs another item"
	set cycles 50
	set continuous no
	set break_if_on_first yes
	set break_if never
	setcycle 0 correct_response 13
	setcycle 0 S1 13
	setcycle 0 S2 6
	setcycle 0 S3 0
	setcycle 0 S4 0
	setcycle 0 S5 0
	setcycle 0 S6 0
	setcycle 0 S7 0
	setcycle 0 S8 0
	setcycle 0 A1 13
	setcycle 0 A2 1
	setcycle 0 A3 6
	setcycle 0 A4 3
	setcycle 0 A5 5
	setcycle 0 A6 9
	setcycle 0 A7 2
	setcycle 0 A8 4
	setcycle 0 G1X -160
	setcycle 0 G1Y 0
	setcycle 0 G2X 160
	setcycle 0 G2Y 0
	setcycle 0 G3X -544
	setcycle 0 G3Y 256
	setcycle 0 G4X -544
	setcycle 0 G4Y 256
	setcycle 0 G5X -544
	setcycle 0 G5Y 256
	setcycle 0 G6X -544
	setcycle 0 G6Y 256
	setcycle 0 G7X -544
	setcycle 0 G7Y 256
	setcycle 0 G8X -544
	setcycle 0 G8Y 256
	setcycle 0 WAKTU 5000
	setcycle 1 correct_response 23
	setcycle 1 S1 7
	setcycle 1 S2 24
	setcycle 1 S3 0
	setcycle 1 S4 0
	setcycle 1 S5 0
	setcycle 1 S6 0
	setcycle 1 S7 0
	setcycle 1 S8 0
	setcycle 1 A1 2
	setcycle 1 A2 7
	setcycle 1 A3 24
	setcycle 1 A4 17
	setcycle 1 A5 3
	setcycle 1 A6 4
	setcycle 1 A7 5
	setcycle 1 A8 16
	setcycle 1 G1X -160
	setcycle 1 G1Y 0
	setcycle 1 G2X 160
	setcycle 1 G2Y 0
	setcycle 1 G3X -544
	setcycle 1 G3Y 256
	setcycle 1 G4X -544
	setcycle 1 G4Y 256
	setcycle 1 G5X -544
	setcycle 1 G5Y 256
	setcycle 1 G6X -544
	setcycle 1 G6Y 256
	setcycle 1 G7X -544
	setcycle 1 G7Y 256
	setcycle 1 G8X -544
	setcycle 1 G8Y 256
	setcycle 1 WAKTU 5000
	setcycle 2 correct_response 47
	setcycle 2 S1 5
	setcycle 2 S2 1
	setcycle 2 S3 0
	setcycle 2 S4 0
	setcycle 2 S5 0
	setcycle 2 S6 0
	setcycle 2 S7 0
	setcycle 2 S8 0
	setcycle 2 A1 9
	setcycle 2 A2 10
	setcycle 2 A3 7
	setcycle 2 A4 5
	setcycle 2 A5 15
	setcycle 2 A6 6
	setcycle 2 A7 1
	setcycle 2 A8 3
	setcycle 2 G1X -160
	setcycle 2 G1Y 0
	setcycle 2 G2X 160
	setcycle 2 G2Y 0
	setcycle 2 G3X -544
	setcycle 2 G3Y 256
	setcycle 2 G4X -544
	setcycle 2 G4Y 256
	setcycle 2 G5X -544
	setcycle 2 G5Y 256
	setcycle 2 G6X -544
	setcycle 2 G6Y 256
	setcycle 2 G7X -544
	setcycle 2 G7Y 256
	setcycle 2 G8X -544
	setcycle 2 G8Y 256
	setcycle 2 WAKTU 5000
	setcycle 3 correct_response 15
	setcycle 3 S1 2
	setcycle 3 S2 18
	setcycle 3 S3 0
	setcycle 3 S4 0
	setcycle 3 S5 0
	setcycle 3 S6 0
	setcycle 3 S7 0
	setcycle 3 S8 0
	setcycle 3 A1 2
	setcycle 3 A2 8
	setcycle 3 A3 6
	setcycle 3 A4 4
	setcycle 3 A5 18
	setcycle 3 A6 11
	setcycle 3 A7 7
	setcycle 3 A8 22
	setcycle 3 G1X -160
	setcycle 3 G1Y 0
	setcycle 3 G2X 160
	setcycle 3 G2Y 0
	setcycle 3 G3X -544
	setcycle 3 G3Y 256
	setcycle 3 G4X -544
	setcycle 3 G4Y 256
	setcycle 3 G5X -544
	setcycle 3 G5Y 256
	setcycle 3 G6X -544
	setcycle 3 G6Y 256
	setcycle 3 G7X -544
	setcycle 3 G7Y 256
	setcycle 3 G8X -544
	setcycle 3 G8Y 256
	setcycle 3 WAKTU 5000
	setcycle 4 correct_response 67
	setcycle 4 S1 14
	setcycle 4 S2 15
	setcycle 4 S3 0
	setcycle 4 S4 0
	setcycle 4 S5 0
	setcycle 4 S6 0
	setcycle 4 S7 0
	setcycle 4 S8 0
	setcycle 4 A1 5
	setcycle 4 A2 7
	setcycle 4 A3 4
	setcycle 4 A4 8
	setcycle 4 A5 9
	setcycle 4 A6 14
	setcycle 4 A7 15
	setcycle 4 A8 1
	setcycle 4 G1X -160
	setcycle 4 G1Y 0
	setcycle 4 G2X 160
	setcycle 4 G2Y 0
	setcycle 4 G3X -544
	setcycle 4 G3Y 256
	setcycle 4 G4X -544
	setcycle 4 G4Y 256
	setcycle 4 G5X -544
	setcycle 4 G5Y 256
	setcycle 4 G6X -544
	setcycle 4 G6Y 256
	setcycle 4 G7X -544
	setcycle 4 G7Y 256
	setcycle 4 G8X -544
	setcycle 4 G8Y 256
	setcycle 4 WAKTU 5000
	setcycle 5 correct_response 45
	setcycle 5 S1 15
	setcycle 5 S2 18
	setcycle 5 S3 0
	setcycle 5 S4 0
	setcycle 5 S5 0
	setcycle 5 S6 0
	setcycle 5 S7 0
	setcycle 5 S8 0
	setcycle 5 A1 3
	setcycle 5 A2 5
	setcycle 5 A3 9
	setcycle 5 A4 15
	setcycle 5 A5 18
	setcycle 5 A6 13
	setcycle 5 A7 16
	setcycle 5 A8 20
	setcycle 5 G1X -160
	setcycle 5 G1Y 0
	setcycle 5 G2X 160
	setcycle 5 G2Y 0
	setcycle 5 G3X -544
	setcycle 5 G3Y 256
	setcycle 5 G4X -544
	setcycle 5 G4Y 256
	setcycle 5 G5X -544
	setcycle 5 G5Y 256
	setcycle 5 G6X -544
	setcycle 5 G6Y 256
	setcycle 5 G7X -544
	setcycle 5 G7Y 256
	setcycle 5 G8X -544
	setcycle 5 G8Y 256
	setcycle 5 WAKTU 5000
	setcycle 6 correct_response 67
	setcycle 6 S1 9
	setcycle 6 S2 4
	setcycle 6 S3 0
	setcycle 6 S4 0
	setcycle 6 S5 0
	setcycle 6 S6 0
	setcycle 6 S7 0
	setcycle 6 S8 0
	setcycle 6 A1 1
	setcycle 6 A2 13
	setcycle 6 A3 10
	setcycle 6 A4 7
	setcycle 6 A5 24
	setcycle 6 A6 9
	setcycle 6 A7 4
	setcycle 6 A8 5
	setcycle 6 G1X -160
	setcycle 6 G1Y 0
	setcycle 6 G2X 160
	setcycle 6 G2Y 0
	setcycle 6 G3X -544
	setcycle 6 G3Y 256
	setcycle 6 G4X -544
	setcycle 6 G4Y 256
	setcycle 6 G5X -544
	setcycle 6 G5Y 256
	setcycle 6 G6X -544
	setcycle 6 G6Y 256
	setcycle 6 G7X -544
	setcycle 6 G7Y 256
	setcycle 6 G8X -544
	setcycle 6 G8Y 256
	setcycle 6 WAKTU 5000
	setcycle 7 correct_response 28
	setcycle 7 S1 26
	setcycle 7 S2 28
	setcycle 7 S3 0
	setcycle 7 S4 0
	setcycle 7 S5 0
	setcycle 7 S6 0
	setcycle 7 S7 0
	setcycle 7 S8 0
	setcycle 7 A1 3
	setcycle 7 A2 26
	setcycle 7 A3 7
	setcycle 7 A4 8
	setcycle 7 A5 10
	setcycle 7 A6 11
	setcycle 7 A7 5
	setcycle 7 A8 28
	setcycle 7 G1X -160
	setcycle 7 G1Y 0
	setcycle 7 G2X 160
	setcycle 7 G2Y 0
	setcycle 7 G3X -544
	setcycle 7 G3Y 256
	setcycle 7 G4X -544
	setcycle 7 G4Y 256
	setcycle 7 G5X -544
	setcycle 7 G5Y 256
	setcycle 7 G6X -544
	setcycle 7 G6Y 256
	setcycle 7 G7X -544
	setcycle 7 G7Y 256
	setcycle 7 G8X -544
	setcycle 7 G8Y 256
	setcycle 7 WAKTU 5000
	setcycle 8 correct_response 45
	setcycle 8 S1 5
	setcycle 8 S2 11
	setcycle 8 S3 0
	setcycle 8 S4 0
	setcycle 8 S5 0
	setcycle 8 S6 0
	setcycle 8 S7 0
	setcycle 8 S8 0
	setcycle 8 A1 14
	setcycle 8 A2 25
	setcycle 8 A3 18
	setcycle 8 A4 5
	setcycle 8 A5 11
	setcycle 8 A6 2
	setcycle 8 A7 4
	setcycle 8 A8 9
	setcycle 8 G1X -160
	setcycle 8 G1Y 0
	setcycle 8 G2X 160
	setcycle 8 G2Y 0
	setcycle 8 G3X -544
	setcycle 8 G3Y 256
	setcycle 8 G4X -544
	setcycle 8 G4Y 256
	setcycle 8 G5X -544
	setcycle 8 G5Y 256
	setcycle 8 G6X -544
	setcycle 8 G6Y 256
	setcycle 8 G7X -544
	setcycle 8 G7Y 256
	setcycle 8 G8X -544
	setcycle 8 G8Y 256
	setcycle 8 WAKTU 5000
	setcycle 9 correct_response 23
	setcycle 9 S1 13
	setcycle 9 S2 11
	setcycle 9 S3 0
	setcycle 9 S4 0
	setcycle 9 S5 0
	setcycle 9 S6 0
	setcycle 9 S7 0
	setcycle 9 S8 0
	setcycle 9 A1 1
	setcycle 9 A2 13
	setcycle 9 A3 11
	setcycle 9 A4 3
	setcycle 9 A5 4
	setcycle 9 A6 5
	setcycle 9 A7 7
	setcycle 9 A8 8
	setcycle 9 G1X -160
	setcycle 9 G1Y 0
	setcycle 9 G2X 160
	setcycle 9 G2Y 0
	setcycle 9 G3X -544
	setcycle 9 G3Y 256
	setcycle 9 G4X -544
	setcycle 9 G4Y 256
	setcycle 9 G5X -544
	setcycle 9 G5Y 256
	setcycle 9 G6X -544
	setcycle 9 G6Y 256
	setcycle 9 G7X -544
	setcycle 9 G7Y 256
	setcycle 9 G8X -544
	setcycle 9 G8Y 256
	setcycle 9 WAKTU 5000
	setcycle 10 correct_response 135
	setcycle 10 S1 14
	setcycle 10 S2 30
	setcycle 10 S3 24
	setcycle 10 S4 0
	setcycle 10 S5 0
	setcycle 10 S6 0
	setcycle 10 S7 0
	setcycle 10 S8 0
	setcycle 10 A1 14
	setcycle 10 A2 7
	setcycle 10 A3 30
	setcycle 10 A4 5
	setcycle 10 A5 24
	setcycle 10 A6 8
	setcycle 10 A7 9
	setcycle 10 A8 15
	setcycle 10 G1X -288
	setcycle 10 G1Y 0
	setcycle 10 G2X 0
	setcycle 10 G2Y 0
	setcycle 10 G3X 288
	setcycle 10 G3Y 0
	setcycle 10 G4X -544
	setcycle 10 G4Y 256
	setcycle 10 G5X -544
	setcycle 10 G5Y 256
	setcycle 10 G6X -544
	setcycle 10 G6Y 256
	setcycle 10 G7X -544
	setcycle 10 G7Y 256
	setcycle 10 G8X -544
	setcycle 10 G8Y 256
	setcycle 10 WAKTU 7500
	setcycle 11 correct_response 246
	setcycle 11 S1 11
	setcycle 11 S2 9
	setcycle 11 S3 5
	setcycle 11 S4 0
	setcycle 11 S5 0
	setcycle 11 S6 0
	setcycle 11 S7 0
	setcycle 11 S8 0
	setcycle 11 A1 13
	setcycle 11 A2 11
	setcycle 11 A3 7
	setcycle 11 A4 9
	setcycle 11 A5 4
	setcycle 11 A6 5
	setcycle 11 A7 6
	setcycle 11 A8 1
	setcycle 11 G1X -288
	setcycle 11 G1Y 0
	setcycle 11 G2X 0
	setcycle 11 G2Y 0
	setcycle 11 G3X 288
	setcycle 11 G3Y 0
	setcycle 11 G4X -544
	setcycle 11 G4Y 256
	setcycle 11 G5X -544
	setcycle 11 G5Y 256
	setcycle 11 G6X -544
	setcycle 11 G6Y 256
	setcycle 11 G7X -544
	setcycle 11 G7Y 256
	setcycle 11 G8X -544
	setcycle 11 G8Y 256
	setcycle 11 WAKTU 7500
	setcycle 12 correct_response 145
	setcycle 12 S1 10
	setcycle 12 S2 23
	setcycle 12 S3 16
	setcycle 12 S4 0
	setcycle 12 S5 0
	setcycle 12 S6 0
	setcycle 12 S7 0
	setcycle 12 S8 0
	setcycle 12 A1 10
	setcycle 12 A2 14
	setcycle 12 A3 8
	setcycle 12 A4 23
	setcycle 12 A5 16
	setcycle 12 A6 9
	setcycle 12 A7 7
	setcycle 12 A8 6
	setcycle 12 G1X -288
	setcycle 12 G1Y 0
	setcycle 12 G2X 0
	setcycle 12 G2Y 0
	setcycle 12 G3X 288
	setcycle 12 G3Y 0
	setcycle 12 G4X -544
	setcycle 12 G4Y 256
	setcycle 12 G5X -544
	setcycle 12 G5Y 256
	setcycle 12 G6X -544
	setcycle 12 G6Y 256
	setcycle 12 G7X -544
	setcycle 12 G7Y 256
	setcycle 12 G8X -544
	setcycle 12 G8Y 256
	setcycle 12 WAKTU 7500
	setcycle 13 correct_response 234
	setcycle 13 S1 6
	setcycle 13 S2 9
	setcycle 13 S3 19
	setcycle 13 S4 0
	setcycle 13 S5 0
	setcycle 13 S6 0
	setcycle 13 S7 0
	setcycle 13 S8 0
	setcycle 13 A1 1
	setcycle 13 A2 6
	setcycle 13 A3 9
	setcycle 13 A4 19
	setcycle 13 A5 17
	setcycle 13 A6 5
	setcycle 13 A7 3
	setcycle 13 A8 2
	setcycle 13 G1X -288
	setcycle 13 G1Y 0
	setcycle 13 G2X 0
	setcycle 13 G2Y 0
	setcycle 13 G3X 288
	setcycle 13 G3Y 0
	setcycle 13 G4X -544
	setcycle 13 G4Y 256
	setcycle 13 G5X -544
	setcycle 13 G5Y 256
	setcycle 13 G6X -544
	setcycle 13 G6Y 256
	setcycle 13 G7X -544
	setcycle 13 G7Y 256
	setcycle 13 G8X -544
	setcycle 13 G8Y 256
	setcycle 13 WAKTU 7500
	setcycle 14 correct_response 578
	setcycle 14 S1 10
	setcycle 14 S2 5
	setcycle 14 S3 17
	setcycle 14 S4 0
	setcycle 14 S5 0
	setcycle 14 S6 0
	setcycle 14 S7 0
	setcycle 14 S8 0
	setcycle 14 A1 19
	setcycle 14 A2 13
	setcycle 14 A3 6
	setcycle 14 A4 4
	setcycle 14 A5 10
	setcycle 14 A6 3
	setcycle 14 A7 5
	setcycle 14 A8 17
	setcycle 14 G1X -288
	setcycle 14 G1Y 0
	setcycle 14 G2X 0
	setcycle 14 G2Y 0
	setcycle 14 G3X 288
	setcycle 14 G3Y 0
	setcycle 14 G4X -544
	setcycle 14 G4Y 256
	setcycle 14 G5X -544
	setcycle 14 G5Y 256
	setcycle 14 G6X -544
	setcycle 14 G6Y 256
	setcycle 14 G7X -544
	setcycle 14 G7Y 256
	setcycle 14 G8X -544
	setcycle 14 G8Y 256
	setcycle 14 WAKTU 7500
	setcycle 15 correct_response 467
	setcycle 15 S1 19
	setcycle 15 S2 23
	setcycle 15 S3 30
	setcycle 15 S4 0
	setcycle 15 S5 0
	setcycle 15 S6 0
	setcycle 15 S7 0
	setcycle 15 S8 0
	setcycle 15 A1 11
	setcycle 15 A2 9
	setcycle 15 A3 8
	setcycle 15 A4 19
	setcycle 15 A5 7
	setcycle 15 A6 23
	setcycle 15 A7 30
	setcycle 15 A8 10
	setcycle 15 G1X -288
	setcycle 15 G1Y 0
	setcycle 15 G2X 0
	setcycle 15 G2Y 0
	setcycle 15 G3X 288
	setcycle 15 G3Y 0
	setcycle 15 G4X -544
	setcycle 15 G4Y 256
	setcycle 15 G5X -544
	setcycle 15 G5Y 256
	setcycle 15 G6X -544
	setcycle 15 G6Y 256
	setcycle 15 G7X -544
	setcycle 15 G7Y 256
	setcycle 15 G8X -544
	setcycle 15 G8Y 256
	setcycle 15 WAKTU 7500
	setcycle 16 correct_response 567
	setcycle 16 S1 20
	setcycle 16 S2 6
	setcycle 16 S3 16
	setcycle 16 S4 0
	setcycle 16 S5 0
	setcycle 16 S6 0
	setcycle 16 S7 0
	setcycle 16 S8 0
	setcycle 16 A1 2
	setcycle 16 A2 12
	setcycle 16 A3 4
	setcycle 16 A4 1
	setcycle 16 A5 20
	setcycle 16 A6 6
	setcycle 16 A7 16
	setcycle 16 A8 5
	setcycle 16 G1X -288
	setcycle 16 G1Y 0
	setcycle 16 G2X 0
	setcycle 16 G2Y 0
	setcycle 16 G3X 288
	setcycle 16 G3Y 0
	setcycle 16 G4X -544
	setcycle 16 G4Y 256
	setcycle 16 G5X -544
	setcycle 16 G5Y 256
	setcycle 16 G6X -544
	setcycle 16 G6Y 256
	setcycle 16 G7X -544
	setcycle 16 G7Y 256
	setcycle 16 G8X -544
	setcycle 16 G8Y 256
	setcycle 16 WAKTU 7500
	setcycle 17 correct_response 368
	setcycle 17 S1 13
	setcycle 17 S2 7
	setcycle 17 S3 20
	setcycle 17 S4 0
	setcycle 17 S5 0
	setcycle 17 S6 0
	setcycle 17 S7 0
	setcycle 17 S8 0
	setcycle 17 A1 17
	setcycle 17 A2 16
	setcycle 17 A3 13
	setcycle 17 A4 6
	setcycle 17 A5 5
	setcycle 17 A6 7
	setcycle 17 A7 9
	setcycle 17 A8 20
	setcycle 17 G1X -288
	setcycle 17 G1Y 0
	setcycle 17 G2X 0
	setcycle 17 G2Y 0
	setcycle 17 G3X 288
	setcycle 17 G3Y 0
	setcycle 17 G4X -544
	setcycle 17 G4Y 256
	setcycle 17 G5X -544
	setcycle 17 G5Y 256
	setcycle 17 G6X -544
	setcycle 17 G6Y 256
	setcycle 17 G7X -544
	setcycle 17 G7Y 256
	setcycle 17 G8X -544
	setcycle 17 G8Y 256
	setcycle 17 WAKTU 7500
	setcycle 18 correct_response 258
	setcycle 18 S1 27
	setcycle 18 S2 5
	setcycle 18 S3 14
	setcycle 18 S4 0
	setcycle 18 S5 0
	setcycle 18 S6 0
	setcycle 18 S7 0
	setcycle 18 S8 0
	setcycle 18 A1 15
	setcycle 18 A2 27
	setcycle 18 A3 1
	setcycle 18 A4 9
	setcycle 18 A5 5
	setcycle 18 A6 13
	setcycle 18 A7 12
	setcycle 18 A8 14
	setcycle 18 G1X -288
	setcycle 18 G1Y 0
	setcycle 18 G2X 0
	setcycle 18 G2Y 0
	setcycle 18 G3X 288
	setcycle 18 G3Y 0
	setcycle 18 G4X -544
	setcycle 18 G4Y 256
	setcycle 18 G5X -544
	setcycle 18 G5Y 256
	setcycle 18 G6X -544
	setcycle 18 G6Y 256
	setcycle 18 G7X -544
	setcycle 18 G7Y 256
	setcycle 18 G8X -544
	setcycle 18 G8Y 256
	setcycle 18 WAKTU 7500
	setcycle 19 correct_response 157
	setcycle 19 S1 14
	setcycle 19 S2 25
	setcycle 19 S3 8
	setcycle 19 S4 0
	setcycle 19 S5 0
	setcycle 19 S6 0
	setcycle 19 S7 0
	setcycle 19 S8 0
	setcycle 19 A1 14
	setcycle 19 A2 7
	setcycle 19 A3 6
	setcycle 19 A4 5
	setcycle 19 A5 25
	setcycle 19 A6 13
	setcycle 19 A7 8
	setcycle 19 A8 9
	setcycle 19 G1X -288
	setcycle 19 G1Y 0
	setcycle 19 G2X 0
	setcycle 19 G2Y 0
	setcycle 19 G3X 288
	setcycle 19 G3Y 0
	setcycle 19 G4X -544
	setcycle 19 G4Y 256
	setcycle 19 G5X -544
	setcycle 19 G5Y 256
	setcycle 19 G6X -544
	setcycle 19 G6Y 256
	setcycle 19 G7X -544
	setcycle 19 G7Y 256
	setcycle 19 G8X -544
	setcycle 19 G8Y 256
	setcycle 19 WAKTU 7500
	setcycle 20 correct_response 3457
	setcycle 20 S1 19
	setcycle 20 S2 11
	setcycle 20 S3 15
	setcycle 20 S4 30
	setcycle 20 S5 0
	setcycle 20 S6 0
	setcycle 20 S7 0
	setcycle 20 S8 0
	setcycle 20 A1 1
	setcycle 20 A2 6
	setcycle 20 A3 19
	setcycle 20 A4 11
	setcycle 20 A5 15
	setcycle 20 A6 10
	setcycle 20 A7 30
	setcycle 20 A8 7
	setcycle 20 G1X -384
	setcycle 20 G1Y 0
	setcycle 20 G2X -128
	setcycle 20 G2Y 0
	setcycle 20 G3X 128
	setcycle 20 G3Y 0
	setcycle 20 G4X 384
	setcycle 20 G4Y 0
	setcycle 20 G5X -544
	setcycle 20 G5Y 256
	setcycle 20 G6X -544
	setcycle 20 G6Y 256
	setcycle 20 G7X -544
	setcycle 20 G7Y 256
	setcycle 20 G8X -544
	setcycle 20 G8Y 256
	setcycle 20 WAKTU 10000
	setcycle 21 correct_response 1257
	setcycle 21 S1 19
	setcycle 21 S2 14
	setcycle 21 S3 24
	setcycle 21 S4 1
	setcycle 21 S5 0
	setcycle 21 S6 0
	setcycle 21 S7 0
	setcycle 21 S8 0
	setcycle 21 A1 19
	setcycle 21 A2 14
	setcycle 21 A3 7
	setcycle 21 A4 4
	setcycle 21 A5 24
	setcycle 21 A6 12
	setcycle 21 A7 1
	setcycle 21 A8 5
	setcycle 21 G1X -384
	setcycle 21 G1Y 0
	setcycle 21 G2X -128
	setcycle 21 G2Y 0
	setcycle 21 G3X 128
	setcycle 21 G3Y 0
	setcycle 21 G4X 384
	setcycle 21 G4Y 0
	setcycle 21 G5X -544
	setcycle 21 G5Y 256
	setcycle 21 G6X -544
	setcycle 21 G6Y 256
	setcycle 21 G7X -544
	setcycle 21 G7Y 256
	setcycle 21 G8X -544
	setcycle 21 G8Y 256
	setcycle 21 WAKTU 10000
	setcycle 22 correct_response 2467
	setcycle 22 S1 4
	setcycle 22 S2 2
	setcycle 22 S3 14
	setcycle 22 S4 6
	setcycle 22 S5 0
	setcycle 22 S6 0
	setcycle 22 S7 0
	setcycle 22 S8 0
	setcycle 22 A1 11
	setcycle 22 A2 4
	setcycle 22 A3 19
	setcycle 22 A4 2
	setcycle 22 A5 17
	setcycle 22 A6 14
	setcycle 22 A7 6
	setcycle 22 A8 7
	setcycle 22 G1X -384
	setcycle 22 G1Y 0
	setcycle 22 G2X -128
	setcycle 22 G2Y 0
	setcycle 22 G3X 128
	setcycle 22 G3Y 0
	setcycle 22 G4X 384
	setcycle 22 G4Y 0
	setcycle 22 G5X -544
	setcycle 22 G5Y 256
	setcycle 22 G6X -544
	setcycle 22 G6Y 256
	setcycle 22 G7X -544
	setcycle 22 G7Y 256
	setcycle 22 G8X -544
	setcycle 22 G8Y 256
	setcycle 22 WAKTU 10000
	setcycle 23 correct_response 1568
	setcycle 23 S1 9
	setcycle 23 S2 13
	setcycle 23 S3 5
	setcycle 23 S4 23
	setcycle 23 S5 0
	setcycle 23 S6 0
	setcycle 23 S7 0
	setcycle 23 S8 0
	setcycle 23 A1 9
	setcycle 23 A2 1
	setcycle 23 A3 14
	setcycle 23 A4 8
	setcycle 23 A5 13
	setcycle 23 A6 5
	setcycle 23 A7 21
	setcycle 23 A8 23
	setcycle 23 G1X -384
	setcycle 23 G1Y 0
	setcycle 23 G2X -128
	setcycle 23 G2Y 0
	setcycle 23 G3X 128
	setcycle 23 G3Y 0
	setcycle 23 G4X 384
	setcycle 23 G4Y 0
	setcycle 23 G5X -544
	setcycle 23 G5Y 256
	setcycle 23 G6X -544
	setcycle 23 G6Y 256
	setcycle 23 G7X -544
	setcycle 23 G7Y 256
	setcycle 23 G8X -544
	setcycle 23 G8Y 256
	setcycle 23 WAKTU 10000
	setcycle 24 correct_response 2346
	setcycle 24 S1 16
	setcycle 24 S2 23
	setcycle 24 S3 22
	setcycle 24 S4 11
	setcycle 24 S5 0
	setcycle 24 S6 0
	setcycle 24 S7 0
	setcycle 24 S8 0
	setcycle 24 A1 5
	setcycle 24 A2 16
	setcycle 24 A3 23
	setcycle 24 A4 22
	setcycle 24 A5 4
	setcycle 24 A6 11
	setcycle 24 A7 3
	setcycle 24 A8 2
	setcycle 24 G1X -384
	setcycle 24 G1Y 0
	setcycle 24 G2X -128
	setcycle 24 G2Y 0
	setcycle 24 G3X 128
	setcycle 24 G3Y 0
	setcycle 24 G4X 384
	setcycle 24 G4Y 0
	setcycle 24 G5X -544
	setcycle 24 G5Y 256
	setcycle 24 G6X -544
	setcycle 24 G6Y 256
	setcycle 24 G7X -544
	setcycle 24 G7Y 256
	setcycle 24 G8X -544
	setcycle 24 G8Y 256
	setcycle 24 WAKTU 10000
	setcycle 25 correct_response 3456
	setcycle 25 S1 9
	setcycle 25 S2 19
	setcycle 25 S3 12
	setcycle 25 S4 8
	setcycle 25 S5 0
	setcycle 25 S6 0
	setcycle 25 S7 0
	setcycle 25 S8 0
	setcycle 25 A1 2
	setcycle 25 A2 7
	setcycle 25 A3 9
	setcycle 25 A4 19
	setcycle 25 A5 12
	setcycle 25 A6 8
	setcycle 25 A7 4
	setcycle 25 A8 10
	setcycle 25 G1X -384
	setcycle 25 G1Y 0
	setcycle 25 G2X -128
	setcycle 25 G2Y 0
	setcycle 25 G3X 128
	setcycle 25 G3Y 0
	setcycle 25 G4X 384
	setcycle 25 G4Y 0
	setcycle 25 G5X -544
	setcycle 25 G5Y 256
	setcycle 25 G6X -544
	setcycle 25 G6Y 256
	setcycle 25 G7X -544
	setcycle 25 G7Y 256
	setcycle 25 G8X -544
	setcycle 25 G8Y 256
	setcycle 25 WAKTU 10000
	setcycle 26 correct_response 1457
	setcycle 26 S1 8
	setcycle 26 S2 22
	setcycle 26 S3 16
	setcycle 26 S4 18
	setcycle 26 S5 0
	setcycle 26 S6 0
	setcycle 26 S7 0
	setcycle 26 S8 0
	setcycle 26 A1 8
	setcycle 26 A2 6
	setcycle 26 A3 10
	setcycle 26 A4 22
	setcycle 26 A5 16
	setcycle 26 A6 21
	setcycle 26 A7 18
	setcycle 26 A8 23
	setcycle 26 G1X -384
	setcycle 26 G1Y 0
	setcycle 26 G2X -128
	setcycle 26 G2Y 0
	setcycle 26 G3X 128
	setcycle 26 G3Y 0
	setcycle 26 G4X 384
	setcycle 26 G4Y 0
	setcycle 26 G5X -544
	setcycle 26 G5Y 256
	setcycle 26 G6X -544
	setcycle 26 G6Y 256
	setcycle 26 G7X -544
	setcycle 26 G7Y 256
	setcycle 26 G8X -544
	setcycle 26 G8Y 256
	setcycle 26 WAKTU 10000
	setcycle 27 correct_response 2358
	setcycle 27 S1 27
	setcycle 27 S2 3
	setcycle 27 S3 22
	setcycle 27 S4 23
	setcycle 27 S5 0
	setcycle 27 S6 0
	setcycle 27 S7 0
	setcycle 27 S8 0
	setcycle 27 A1 2
	setcycle 27 A2 27
	setcycle 27 A3 3
	setcycle 27 A4 13
	setcycle 27 A5 22
	setcycle 27 A6 16
	setcycle 27 A7 25
	setcycle 27 A8 23
	setcycle 27 G1X -384
	setcycle 27 G1Y 0
	setcycle 27 G2X -128
	setcycle 27 G2Y 0
	setcycle 27 G3X 128
	setcycle 27 G3Y 0
	setcycle 27 G4X 384
	setcycle 27 G4Y 0
	setcycle 27 G5X -544
	setcycle 27 G5Y 256
	setcycle 27 G6X -544
	setcycle 27 G6Y 256
	setcycle 27 G7X -544
	setcycle 27 G7Y 256
	setcycle 27 G8X -544
	setcycle 27 G8Y 256
	setcycle 27 WAKTU 10000
	setcycle 28 correct_response 3567
	setcycle 28 S1 2
	setcycle 28 S2 22
	setcycle 28 S3 5
	setcycle 28 S4 6
	setcycle 28 S5 0
	setcycle 28 S6 0
	setcycle 28 S7 0
	setcycle 28 S8 0
	setcycle 28 A1 11
	setcycle 28 A2 12
	setcycle 28 A3 2
	setcycle 28 A4 7
	setcycle 28 A5 22
	setcycle 28 A6 5
	setcycle 28 A7 6
	setcycle 28 A8 10
	setcycle 28 G1X -384
	setcycle 28 G1Y 0
	setcycle 28 G2X -128
	setcycle 28 G2Y 0
	setcycle 28 G3X 128
	setcycle 28 G3Y 0
	setcycle 28 G4X 384
	setcycle 28 G4Y 0
	setcycle 28 G5X -544
	setcycle 28 G5Y 256
	setcycle 28 G6X -544
	setcycle 28 G6Y 256
	setcycle 28 G7X -544
	setcycle 28 G7Y 256
	setcycle 28 G8X -544
	setcycle 28 G8Y 256
	setcycle 28 WAKTU 10000
	setcycle 29 correct_response 2578
	setcycle 29 S1 8
	setcycle 29 S2 17
	setcycle 29 S3 20
	setcycle 29 S4 10
	setcycle 29 S5 0
	setcycle 29 S6 0
	setcycle 29 S7 0
	setcycle 29 S8 0
	setcycle 29 A1 5
	setcycle 29 A2 8
	setcycle 29 A3 9
	setcycle 29 A4 11
	setcycle 29 A5 17
	setcycle 29 A6 13
	setcycle 29 A7 20
	setcycle 29 A8 10
	setcycle 29 G1X -384
	setcycle 29 G1Y 0
	setcycle 29 G2X -128
	setcycle 29 G2Y 0
	setcycle 29 G3X 128
	setcycle 29 G3Y 0
	setcycle 29 G4X 384
	setcycle 29 G4Y 0
	setcycle 29 G5X -544
	setcycle 29 G5Y 256
	setcycle 29 G6X -544
	setcycle 29 G6Y 256
	setcycle 29 G7X -544
	setcycle 29 G7Y 256
	setcycle 29 G8X -544
	setcycle 29 G8Y 256
	setcycle 29 WAKTU 10000
	setcycle 30 correct_response 12367
	setcycle 30 S1 8
	setcycle 30 S2 14
	setcycle 30 S3 13
	setcycle 30 S4 10
	setcycle 30 S5 12
	setcycle 30 S6 0
	setcycle 30 S7 0
	setcycle 30 S8 0
	setcycle 30 A1 8
	setcycle 30 A2 14
	setcycle 30 A3 13
	setcycle 30 A4 9
	setcycle 30 A5 2
	setcycle 30 A6 10
	setcycle 30 A7 12
	setcycle 30 A8 6
	setcycle 30 G1X -448
	setcycle 30 G1Y 0
	setcycle 30 G2X -224
	setcycle 30 G2Y 0
	setcycle 30 G3X 0
	setcycle 30 G3Y 0
	setcycle 30 G4X 224
	setcycle 30 G4Y 0
	setcycle 30 G5X 448
	setcycle 30 G5Y 0
	setcycle 30 G6X -544
	setcycle 30 G6Y 256
	setcycle 30 G7X -544
	setcycle 30 G7Y 256
	setcycle 30 G8X -544
	setcycle 30 G8Y 256
	setcycle 30 WAKTU 12500
	setcycle 31 correct_response 25678
	setcycle 31 S1 25
	setcycle 31 S2 4
	setcycle 31 S3 17
	setcycle 31 S4 21
	setcycle 31 S5 19
	setcycle 31 S6 0
	setcycle 31 S7 0
	setcycle 31 S8 0
	setcycle 31 A1 24
	setcycle 31 A2 25
	setcycle 31 A3 3
	setcycle 31 A4 6
	setcycle 31 A5 4
	setcycle 31 A6 17
	setcycle 31 A7 21
	setcycle 31 A8 19
	setcycle 31 G1X -448
	setcycle 31 G1Y 0
	setcycle 31 G2X -224
	setcycle 31 G2Y 0
	setcycle 31 G3X 0
	setcycle 31 G3Y 0
	setcycle 31 G4X 224
	setcycle 31 G4Y 0
	setcycle 31 G5X 448
	setcycle 31 G5Y 0
	setcycle 31 G6X -544
	setcycle 31 G6Y 256
	setcycle 31 G7X -544
	setcycle 31 G7Y 256
	setcycle 31 G8X -544
	setcycle 31 G8Y 256
	setcycle 31 WAKTU 12500
	setcycle 32 correct_response 23567
	setcycle 32 S1 14
	setcycle 32 S2 18
	setcycle 32 S3 26
	setcycle 32 S4 12
	setcycle 32 S5 30
	setcycle 32 S6 0
	setcycle 32 S7 0
	setcycle 32 S8 0
	setcycle 32 A1 5
	setcycle 32 A2 14
	setcycle 32 A3 18
	setcycle 32 A4 6
	setcycle 32 A5 26
	setcycle 32 A6 12
	setcycle 32 A7 30
	setcycle 32 A8 2
	setcycle 32 G1X -448
	setcycle 32 G1Y 0
	setcycle 32 G2X -224
	setcycle 32 G2Y 0
	setcycle 32 G3X 0
	setcycle 32 G3Y 0
	setcycle 32 G4X 224
	setcycle 32 G4Y 0
	setcycle 32 G5X 448
	setcycle 32 G5Y 0
	setcycle 32 G6X -544
	setcycle 32 G6Y 256
	setcycle 32 G7X -544
	setcycle 32 G7Y 256
	setcycle 32 G8X -544
	setcycle 32 G8Y 256
	setcycle 32 WAKTU 12500
	setcycle 33 correct_response 14678
	setcycle 33 S1 3
	setcycle 33 S2 6
	setcycle 33 S3 2
	setcycle 33 S4 4
	setcycle 33 S5 16
	setcycle 33 S6 0
	setcycle 33 S7 0
	setcycle 33 S8 0
	setcycle 33 A1 3
	setcycle 33 A2 9
	setcycle 33 A3 5
	setcycle 33 A4 6
	setcycle 33 A5 11
	setcycle 33 A6 2
	setcycle 33 A7 4
	setcycle 33 A8 16
	setcycle 33 G1X -448
	setcycle 33 G1Y 0
	setcycle 33 G2X -224
	setcycle 33 G2Y 0
	setcycle 33 G3X 0
	setcycle 33 G3Y 0
	setcycle 33 G4X 224
	setcycle 33 G4Y 0
	setcycle 33 G5X 448
	setcycle 33 G5Y 0
	setcycle 33 G6X -544
	setcycle 33 G6Y 256
	setcycle 33 G7X -544
	setcycle 33 G7Y 256
	setcycle 33 G8X -544
	setcycle 33 G8Y 256
	setcycle 33 WAKTU 12500
	setcycle 34 correct_response 23567
	setcycle 34 S1 13
	setcycle 34 S2 12
	setcycle 34 S3 25
	setcycle 34 S4 19
	setcycle 34 S5 21
	setcycle 34 S6 0
	setcycle 34 S7 0
	setcycle 34 S8 0
	setcycle 34 A1 11
	setcycle 34 A2 13
	setcycle 34 A3 12
	setcycle 34 A4 8
	setcycle 34 A5 25
	setcycle 34 A6 19
	setcycle 34 A7 21
	setcycle 34 A8 9
	setcycle 34 G1X -448
	setcycle 34 G1Y 0
	setcycle 34 G2X -224
	setcycle 34 G2Y 0
	setcycle 34 G3X 0
	setcycle 34 G3Y 0
	setcycle 34 G4X 224
	setcycle 34 G4Y 0
	setcycle 34 G5X 448
	setcycle 34 G5Y 0
	setcycle 34 G6X -544
	setcycle 34 G6Y 256
	setcycle 34 G7X -544
	setcycle 34 G7Y 256
	setcycle 34 G8X -544
	setcycle 34 G8Y 256
	setcycle 34 WAKTU 12500
	setcycle 35 correct_response 12568
	setcycle 35 S1 30
	setcycle 35 S2 19
	setcycle 35 S3 6
	setcycle 35 S4 11
	setcycle 35 S5 29
	setcycle 35 S6 0
	setcycle 35 S7 0
	setcycle 35 S8 0
	setcycle 35 A1 30
	setcycle 35 A2 19
	setcycle 35 A3 3
	setcycle 35 A4 9
	setcycle 35 A5 6
	setcycle 35 A6 11
	setcycle 35 A7 7
	setcycle 35 A8 29
	setcycle 35 G1X -448
	setcycle 35 G1Y 0
	setcycle 35 G2X -224
	setcycle 35 G2Y 0
	setcycle 35 G3X 0
	setcycle 35 G3Y 0
	setcycle 35 G4X 224
	setcycle 35 G4Y 0
	setcycle 35 G5X 448
	setcycle 35 G5Y 0
	setcycle 35 G6X -544
	setcycle 35 G6Y 256
	setcycle 35 G7X -544
	setcycle 35 G7Y 256
	setcycle 35 G8X -544
	setcycle 35 G8Y 256
	setcycle 35 WAKTU 12500
	setcycle 36 correct_response 24678
	setcycle 36 S1 11
	setcycle 36 S2 29
	setcycle 36 S3 16
	setcycle 36 S4 1
	setcycle 36 S5 27
	setcycle 36 S6 0
	setcycle 36 S7 0
	setcycle 36 S8 0
	setcycle 36 A1 12
	setcycle 36 A2 11
	setcycle 36 A3 5
	setcycle 36 A4 29
	setcycle 36 A5 8
	setcycle 36 A6 16
	setcycle 36 A7 1
	setcycle 36 A8 27
	setcycle 36 G1X -448
	setcycle 36 G1Y 0
	setcycle 36 G2X -224
	setcycle 36 G2Y 0
	setcycle 36 G3X 0
	setcycle 36 G3Y 0
	setcycle 36 G4X 224
	setcycle 36 G4Y 0
	setcycle 36 G5X 448
	setcycle 36 G5Y 0
	setcycle 36 G6X -544
	setcycle 36 G6Y 256
	setcycle 36 G7X -544
	setcycle 36 G7Y 256
	setcycle 36 G8X -544
	setcycle 36 G8Y 256
	setcycle 36 WAKTU 12500
	setcycle 37 correct_response 23456
	setcycle 37 S1 21
	setcycle 37 S2 26
	setcycle 37 S3 19
	setcycle 37 S4 13
	setcycle 37 S5 2
	setcycle 37 S6 0
	setcycle 37 S7 0
	setcycle 37 S8 0
	setcycle 37 A1 7
	setcycle 37 A2 21
	setcycle 37 A3 26
	setcycle 37 A4 19
	setcycle 37 A5 13
	setcycle 37 A6 2
	setcycle 37 A7 9
	setcycle 37 A8 3
	setcycle 37 G1X -448
	setcycle 37 G1Y 0
	setcycle 37 G2X -224
	setcycle 37 G2Y 0
	setcycle 37 G3X 0
	setcycle 37 G3Y 0
	setcycle 37 G4X 224
	setcycle 37 G4Y 0
	setcycle 37 G5X 448
	setcycle 37 G5Y 0
	setcycle 37 G6X -544
	setcycle 37 G6Y 256
	setcycle 37 G7X -544
	setcycle 37 G7Y 256
	setcycle 37 G8X -544
	setcycle 37 G8Y 256
	setcycle 37 WAKTU 12500
	setcycle 38 correct_response 34678
	setcycle 38 S1 20
	setcycle 38 S2 4
	setcycle 38 S3 22
	setcycle 38 S4 24
	setcycle 38 S5 19
	setcycle 38 S6 0
	setcycle 38 S7 0
	setcycle 38 S8 0
	setcycle 38 A1 16
	setcycle 38 A2 10
	setcycle 38 A3 20
	setcycle 38 A4 4
	setcycle 38 A5 9
	setcycle 38 A6 22
	setcycle 38 A7 24
	setcycle 38 A8 19
	setcycle 38 G1X -448
	setcycle 38 G1Y 0
	setcycle 38 G2X -224
	setcycle 38 G2Y 0
	setcycle 38 G3X 0
	setcycle 38 G3Y 0
	setcycle 38 G4X 224
	setcycle 38 G4Y 0
	setcycle 38 G5X 448
	setcycle 38 G5Y 0
	setcycle 38 G6X -544
	setcycle 38 G6Y 256
	setcycle 38 G7X -544
	setcycle 38 G7Y 256
	setcycle 38 G8X -544
	setcycle 38 G8Y 256
	setcycle 38 WAKTU 12500
	setcycle 39 correct_response 45678
	setcycle 39 S1 9
	setcycle 39 S2 28
	setcycle 39 S3 27
	setcycle 39 S4 30
	setcycle 39 S5 3
	setcycle 39 S6 0
	setcycle 39 S7 0
	setcycle 39 S8 0
	setcycle 39 A1 21
	setcycle 39 A2 25
	setcycle 39 A3 5
	setcycle 39 A4 9
	setcycle 39 A5 28
	setcycle 39 A6 27
	setcycle 39 A7 30
	setcycle 39 A8 3
	setcycle 39 G1X -448
	setcycle 39 G1Y 0
	setcycle 39 G2X -224
	setcycle 39 G2Y 0
	setcycle 39 G3X 0
	setcycle 39 G3Y 0
	setcycle 39 G4X 224
	setcycle 39 G4Y 0
	setcycle 39 G5X 448
	setcycle 39 G5Y 0
	setcycle 39 G6X -544
	setcycle 39 G6Y 256
	setcycle 39 G7X -544
	setcycle 39 G7Y 256
	setcycle 39 G8X -544
	setcycle 39 G8Y 256
	setcycle 39 WAKTU 12500
	setcycle 40 correct_response 135678
	setcycle 40 S1 26
	setcycle 40 S2 27
	setcycle 40 S3 22
	setcycle 40 S4 19
	setcycle 40 S5 10
	setcycle 40 S6 14
	setcycle 40 S7 0
	setcycle 40 S8 0
	setcycle 40 A1 26
	setcycle 40 A2 2
	setcycle 40 A3 27
	setcycle 40 A4 6
	setcycle 40 A5 22
	setcycle 40 A6 19
	setcycle 40 A7 10
	setcycle 40 A8 14
	setcycle 40 G1X -256
	setcycle 40 G1Y -160
	setcycle 40 G2X 0
	setcycle 40 G2Y -160
	setcycle 40 G3X 256
	setcycle 40 G3Y -160
	setcycle 40 G4X -256
	setcycle 40 G4Y 160
	setcycle 40 G5X 0
	setcycle 40 G5Y 160
	setcycle 40 G6X 256
	setcycle 40 G6Y 160
	setcycle 40 G7X -544
	setcycle 40 G7Y 256
	setcycle 40 G8X -544
	setcycle 40 G8Y 256
	setcycle 40 WAKTU 15000
	setcycle 41 correct_response 124567
	setcycle 41 S1 4
	setcycle 41 S2 16
	setcycle 41 S3 19
	setcycle 41 S4 11
	setcycle 41 S5 6
	setcycle 41 S6 28
	setcycle 41 S7 0
	setcycle 41 S8 0
	setcycle 41 A1 4
	setcycle 41 A2 16
	setcycle 41 A3 5
	setcycle 41 A4 19
	setcycle 41 A5 11
	setcycle 41 A6 6
	setcycle 41 A7 28
	setcycle 41 A8 3
	setcycle 41 G1X -256
	setcycle 41 G1Y -160
	setcycle 41 G2X 0
	setcycle 41 G2Y -160
	setcycle 41 G3X 256
	setcycle 41 G3Y -160
	setcycle 41 G4X -256
	setcycle 41 G4Y 160
	setcycle 41 G5X 0
	setcycle 41 G5Y 160
	setcycle 41 G6X 256
	setcycle 41 G6Y 160
	setcycle 41 G7X -544
	setcycle 41 G7Y 256
	setcycle 41 G8X -544
	setcycle 41 G8Y 256
	setcycle 41 WAKTU 15000
	setcycle 42 correct_response 245678
	setcycle 42 S1 13
	setcycle 42 S2 14
	setcycle 42 S3 12
	setcycle 42 S4 3
	setcycle 42 S5 28
	setcycle 42 S6 30
	setcycle 42 S7 0
	setcycle 42 S8 0
	setcycle 42 A1 7
	setcycle 42 A2 13
	setcycle 42 A3 11
	setcycle 42 A4 14
	setcycle 42 A5 12
	setcycle 42 A6 3
	setcycle 42 A7 28
	setcycle 42 A8 30
	setcycle 42 G1X -256
	setcycle 42 G1Y -160
	setcycle 42 G2X 0
	setcycle 42 G2Y -160
	setcycle 42 G3X 256
	setcycle 42 G3Y -160
	setcycle 42 G4X -256
	setcycle 42 G4Y 160
	setcycle 42 G5X 0
	setcycle 42 G5Y 160
	setcycle 42 G6X 256
	setcycle 42 G6Y 160
	setcycle 42 G7X -544
	setcycle 42 G7Y 256
	setcycle 42 G8X -544
	setcycle 42 G8Y 256
	setcycle 42 WAKTU 15000
	setcycle 43 correct_response 123456
	setcycle 43 S1 12
	setcycle 43 S2 2
	setcycle 43 S3 13
	setcycle 43 S4 11
	setcycle 43 S5 1
	setcycle 43 S6 6
	setcycle 43 S7 0
	setcycle 43 S8 0
	setcycle 43 A1 12
	setcycle 43 A2 2
	setcycle 43 A3 13
	setcycle 43 A4 11
	setcycle 43 A5 1
	setcycle 43 A6 6
	setcycle 43 A7 4
	setcycle 43 A8 26
	setcycle 43 G1X -256
	setcycle 43 G1Y -160
	setcycle 43 G2X 0
	setcycle 43 G2Y -160
	setcycle 43 G3X 256
	setcycle 43 G3Y -160
	setcycle 43 G4X -256
	setcycle 43 G4Y 160
	setcycle 43 G5X 0
	setcycle 43 G5Y 160
	setcycle 43 G6X 256
	setcycle 43 G6Y 160
	setcycle 43 G7X -544
	setcycle 43 G7Y 256
	setcycle 43 G8X -544
	setcycle 43 G8Y 256
	setcycle 43 WAKTU 15000
	setcycle 44 correct_response 234567
	setcycle 44 S1 28
	setcycle 44 S2 9
	setcycle 44 S3 5
	setcycle 44 S4 14
	setcycle 44 S5 17
	setcycle 44 S6 7
	setcycle 44 S7 0
	setcycle 44 S8 0
	setcycle 44 A1 4
	setcycle 44 A2 28
	setcycle 44 A3 9
	setcycle 44 A4 5
	setcycle 44 A5 14
	setcycle 44 A6 17
	setcycle 44 A7 7
	setcycle 44 A8 12
	setcycle 44 G1X -256
	setcycle 44 G1Y -160
	setcycle 44 G2X 0
	setcycle 44 G2Y -160
	setcycle 44 G3X 256
	setcycle 44 G3Y -160
	setcycle 44 G4X -256
	setcycle 44 G4Y 160
	setcycle 44 G5X 0
	setcycle 44 G5Y 160
	setcycle 44 G6X 256
	setcycle 44 G6Y 160
	setcycle 44 G7X -544
	setcycle 44 G7Y 256
	setcycle 44 G8X -544
	setcycle 44 G8Y 256
	setcycle 44 WAKTU 15000
	setcycle 45 correct_response 345678
	setcycle 45 S1 2
	setcycle 45 S2 23
	setcycle 45 S3 22
	setcycle 45 S4 7
	setcycle 45 S5 10
	setcycle 45 S6 20
	setcycle 45 S7 0
	setcycle 45 S8 0
	setcycle 45 A1 14
	setcycle 45 A2 6
	setcycle 45 A3 2
	setcycle 45 A4 23
	setcycle 45 A5 22
	setcycle 45 A6 7
	setcycle 45 A7 10
	setcycle 45 A8 20
	setcycle 45 G1X -256
	setcycle 45 G1Y -160
	setcycle 45 G2X 0
	setcycle 45 G2Y -160
	setcycle 45 G3X 256
	setcycle 45 G3Y -160
	setcycle 45 G4X -256
	setcycle 45 G4Y 160
	setcycle 45 G5X 0
	setcycle 45 G5Y 160
	setcycle 45 G6X 256
	setcycle 45 G6Y 160
	setcycle 45 G7X -544
	setcycle 45 G7Y 256
	setcycle 45 G8X -544
	setcycle 45 G8Y 256
	setcycle 45 WAKTU 15000
	setcycle 46 correct_response 245678
	setcycle 46 S1 5
	setcycle 46 S2 30
	setcycle 46 S3 3
	setcycle 46 S4 11
	setcycle 46 S5 19
	setcycle 46 S6 8
	setcycle 46 S7 0
	setcycle 46 S8 0
	setcycle 46 A1 12
	setcycle 46 A2 5
	setcycle 46 A3 1
	setcycle 46 A4 30
	setcycle 46 A5 3
	setcycle 46 A6 11
	setcycle 46 A7 19
	setcycle 46 A8 8
	setcycle 46 G1X -256
	setcycle 46 G1Y -160
	setcycle 46 G2X 0
	setcycle 46 G2Y -160
	setcycle 46 G3X 256
	setcycle 46 G3Y -160
	setcycle 46 G4X -256
	setcycle 46 G4Y 160
	setcycle 46 G5X 0
	setcycle 46 G5Y 160
	setcycle 46 G6X 256
	setcycle 46 G6Y 160
	setcycle 46 G7X -544
	setcycle 46 G7Y 256
	setcycle 46 G8X -544
	setcycle 46 G8Y 256
	setcycle 46 WAKTU 15000
	setcycle 47 correct_response 124567
	setcycle 47 S1 24
	setcycle 47 S2 28
	setcycle 47 S3 9
	setcycle 47 S4 29
	setcycle 47 S5 17
	setcycle 47 S6 19
	setcycle 47 S7 0
	setcycle 47 S8 0
	setcycle 47 A1 24
	setcycle 47 A2 28
	setcycle 47 A3 2
	setcycle 47 A4 9
	setcycle 47 A5 29
	setcycle 47 A6 17
	setcycle 47 A7 19
	setcycle 47 A8 7
	setcycle 47 G1X -256
	setcycle 47 G1Y -160
	setcycle 47 G2X 0
	setcycle 47 G2Y -160
	setcycle 47 G3X 256
	setcycle 47 G3Y -160
	setcycle 47 G4X -256
	setcycle 47 G4Y 160
	setcycle 47 G5X 0
	setcycle 47 G5Y 160
	setcycle 47 G6X 256
	setcycle 47 G6Y 160
	setcycle 47 G7X -544
	setcycle 47 G7Y 256
	setcycle 47 G8X -544
	setcycle 47 G8Y 256
	setcycle 47 WAKTU 15000
	setcycle 48 correct_response 134567
	setcycle 48 S1 21
	setcycle 48 S2 29
	setcycle 48 S3 5
	setcycle 48 S4 28
	setcycle 48 S5 1
	setcycle 48 S6 27
	setcycle 48 S7 0
	setcycle 48 S8 0
	setcycle 48 A1 21
	setcycle 48 A2 3
	setcycle 48 A3 29
	setcycle 48 A4 5
	setcycle 48 A5 28
	setcycle 48 A6 1
	setcycle 48 A7 27
	setcycle 48 A8 6
	setcycle 48 G1X -256
	setcycle 48 G1Y -160
	setcycle 48 G2X 0
	setcycle 48 G2Y -160
	setcycle 48 G3X 256
	setcycle 48 G3Y -160
	setcycle 48 G4X -256
	setcycle 48 G4Y 160
	setcycle 48 G5X 0
	setcycle 48 G5Y 160
	setcycle 48 G6X 256
	setcycle 48 G6Y 160
	setcycle 48 G7X -544
	setcycle 48 G7Y 256
	setcycle 48 G8X -544
	setcycle 48 G8Y 256
	setcycle 48 WAKTU 15000
	setcycle 49 correct_response 145678
	setcycle 49 S1 2
	setcycle 49 S2 29
	setcycle 49 S3 16
	setcycle 49 S4 26
	setcycle 49 S5 7
	setcycle 49 S6 14
	setcycle 49 S7 0
	setcycle 49 S8 0
	setcycle 49 A1 2
	setcycle 49 A2 6
	setcycle 49 A3 8
	setcycle 49 A4 29
	setcycle 49 A5 16
	setcycle 49 A6 26
	setcycle 49 A7 7
	setcycle 49 A8 14
	setcycle 49 G1X -256
	setcycle 49 G1Y -160
	setcycle 49 G2X 0
	setcycle 49 G2Y -160
	setcycle 49 G3X 256
	setcycle 49 G3Y -160
	setcycle 49 G4X -256
	setcycle 49 G4Y 160
	setcycle 49 G5X 0
	setcycle 49 G5Y 160
	setcycle 49 G6X 256
	setcycle 49 G6Y 160
	setcycle 49 G7X -544
	setcycle 49 G7Y 256
	setcycle 49 G8X -544
	setcycle 49 G8Y 256
	setcycle 49 WAKTU 15000
	run seq_capacity

define loop WM_3_Genap
	set source_file ""
	set source table
	set repeat 1
	set order sequential
	set description "Repeatedly runs another item"
	set cycles 50
	set continuous no
	set break_if_on_first yes
	set break_if never
	setcycle 0 correct_response 36
	setcycle 0 S1 27
	setcycle 0 S2 11
	setcycle 0 S3 0
	setcycle 0 S4 0
	setcycle 0 S5 0
	setcycle 0 S6 0
	setcycle 0 S7 0
	setcycle 0 S8 0
	setcycle 0 A1 6
	setcycle 0 A2 3
	setcycle 0 A3 27
	setcycle 0 A4 8
	setcycle 0 A5 1
	setcycle 0 A6 11
	setcycle 0 A7 16
	setcycle 0 A8 2
	setcycle 0 G1X -160
	setcycle 0 G1Y 0
	setcycle 0 G2X 160
	setcycle 0 G2Y 0
	setcycle 0 G3X -544
	setcycle 0 G3Y 256
	setcycle 0 G4X -544
	setcycle 0 G4Y 256
	setcycle 0 G5X -544
	setcycle 0 G5Y 256
	setcycle 0 G6X -544
	setcycle 0 G6Y 256
	setcycle 0 G7X -544
	setcycle 0 G7Y 256
	setcycle 0 G8X -544
	setcycle 0 G8Y 256
	setcycle 0 WAKTU 5000
	setcycle 1 correct_response 15
	setcycle 1 S1 12
	setcycle 1 S2 11
	setcycle 1 S3 0
	setcycle 1 S4 0
	setcycle 1 S5 0
	setcycle 1 S6 0
	setcycle 1 S7 0
	setcycle 1 S8 0
	setcycle 1 A1 12
	setcycle 1 A2 8
	setcycle 1 A3 5
	setcycle 1 A4 4
	setcycle 1 A5 11
	setcycle 1 A6 7
	setcycle 1 A7 9
	setcycle 1 A8 10
	setcycle 1 G1X -160
	setcycle 1 G1Y 0
	setcycle 1 G2X 160
	setcycle 1 G2Y 0
	setcycle 1 G3X -544
	setcycle 1 G3Y 256
	setcycle 1 G4X -544
	setcycle 1 G4Y 256
	setcycle 1 G5X -544
	setcycle 1 G5Y 256
	setcycle 1 G6X -544
	setcycle 1 G6Y 256
	setcycle 1 G7X -544
	setcycle 1 G7Y 256
	setcycle 1 G8X -544
	setcycle 1 G8Y 256
	setcycle 1 WAKTU 5000
	setcycle 2 correct_response 28
	setcycle 2 S1 16
	setcycle 2 S2 1
	setcycle 2 S3 0
	setcycle 2 S4 0
	setcycle 2 S5 0
	setcycle 2 S6 0
	setcycle 2 S7 0
	setcycle 2 S8 0
	setcycle 2 A1 2
	setcycle 2 A2 16
	setcycle 2 A3 5
	setcycle 2 A4 10
	setcycle 2 A5 9
	setcycle 2 A6 3
	setcycle 2 A7 7
	setcycle 2 A8 1
	setcycle 2 G1X -160
	setcycle 2 G1Y 0
	setcycle 2 G2X 160
	setcycle 2 G2Y 0
	setcycle 2 G3X -544
	setcycle 2 G3Y 256
	setcycle 2 G4X -544
	setcycle 2 G4Y 256
	setcycle 2 G5X -544
	setcycle 2 G5Y 256
	setcycle 2 G6X -544
	setcycle 2 G6Y 256
	setcycle 2 G7X -544
	setcycle 2 G7Y 256
	setcycle 2 G8X -544
	setcycle 2 G8Y 256
	setcycle 2 WAKTU 5000
	setcycle 3 correct_response 47
	setcycle 3 S1 4
	setcycle 3 S2 25
	setcycle 3 S3 0
	setcycle 3 S4 0
	setcycle 3 S5 0
	setcycle 3 S6 0
	setcycle 3 S7 0
	setcycle 3 S8 0
	setcycle 3 A1 20
	setcycle 3 A2 16
	setcycle 3 A3 9
	setcycle 3 A4 4
	setcycle 3 A5 5
	setcycle 3 A6 6
	setcycle 3 A7 25
	setcycle 3 A8 11
	setcycle 3 G1X -160
	setcycle 3 G1Y 0
	setcycle 3 G2X 160
	setcycle 3 G2Y 0
	setcycle 3 G3X -544
	setcycle 3 G3Y 256
	setcycle 3 G4X -544
	setcycle 3 G4Y 256
	setcycle 3 G5X -544
	setcycle 3 G5Y 256
	setcycle 3 G6X -544
	setcycle 3 G6Y 256
	setcycle 3 G7X -544
	setcycle 3 G7Y 256
	setcycle 3 G8X -544
	setcycle 3 G8Y 256
	setcycle 3 WAKTU 5000
	setcycle 4 correct_response 13
	setcycle 4 S1 14
	setcycle 4 S2 5
	setcycle 4 S3 0
	setcycle 4 S4 0
	setcycle 4 S5 0
	setcycle 4 S6 0
	setcycle 4 S7 0
	setcycle 4 S8 0
	setcycle 4 A1 14
	setcycle 4 A2 7
	setcycle 4 A3 5
	setcycle 4 A4 8
	setcycle 4 A5 15
	setcycle 4 A6 4
	setcycle 4 A7 6
	setcycle 4 A8 11
	setcycle 4 G1X -160
	setcycle 4 G1Y 0
	setcycle 4 G2X 160
	setcycle 4 G2Y 0
	setcycle 4 G3X -544
	setcycle 4 G3Y 256
	setcycle 4 G4X -544
	setcycle 4 G4Y 256
	setcycle 4 G5X -544
	setcycle 4 G5Y 256
	setcycle 4 G6X -544
	setcycle 4 G6Y 256
	setcycle 4 G7X -544
	setcycle 4 G7Y 256
	setcycle 4 G8X -544
	setcycle 4 G8Y 256
	setcycle 4 WAKTU 5000
	setcycle 5 correct_response 56
	setcycle 5 S1 14
	setcycle 5 S2 25
	setcycle 5 S3 0
	setcycle 5 S4 0
	setcycle 5 S5 0
	setcycle 5 S6 0
	setcycle 5 S7 0
	setcycle 5 S8 0
	setcycle 5 A1 3
	setcycle 5 A2 11
	setcycle 5 A3 1
	setcycle 5 A4 8
	setcycle 5 A5 14
	setcycle 5 A6 25
	setcycle 5 A7 9
	setcycle 5 A8 2
	setcycle 5 G1X -160
	setcycle 5 G1Y 0
	setcycle 5 G2X 160
	setcycle 5 G2Y 0
	setcycle 5 G3X -544
	setcycle 5 G3Y 256
	setcycle 5 G4X -544
	setcycle 5 G4Y 256
	setcycle 5 G5X -544
	setcycle 5 G5Y 256
	setcycle 5 G6X -544
	setcycle 5 G6Y 256
	setcycle 5 G7X -544
	setcycle 5 G7Y 256
	setcycle 5 G8X -544
	setcycle 5 G8Y 256
	setcycle 5 WAKTU 5000
	setcycle 6 correct_response 28
	setcycle 6 S1 23
	setcycle 6 S2 22
	setcycle 6 S3 0
	setcycle 6 S4 0
	setcycle 6 S5 0
	setcycle 6 S6 0
	setcycle 6 S7 0
	setcycle 6 S8 0
	setcycle 6 A1 2
	setcycle 6 A2 23
	setcycle 6 A3 7
	setcycle 6 A4 10
	setcycle 6 A5 13
	setcycle 6 A6 8
	setcycle 6 A7 15
	setcycle 6 A8 22
	setcycle 6 G1X -160
	setcycle 6 G1Y 0
	setcycle 6 G2X 160
	setcycle 6 G2Y 0
	setcycle 6 G3X -544
	setcycle 6 G3Y 256
	setcycle 6 G4X -544
	setcycle 6 G4Y 256
	setcycle 6 G5X -544
	setcycle 6 G5Y 256
	setcycle 6 G6X -544
	setcycle 6 G6Y 256
	setcycle 6 G7X -544
	setcycle 6 G7Y 256
	setcycle 6 G8X -544
	setcycle 6 G8Y 256
	setcycle 6 WAKTU 5000
	setcycle 7 correct_response 14
	setcycle 7 S1 8
	setcycle 7 S2 1
	setcycle 7 S3 0
	setcycle 7 S4 0
	setcycle 7 S5 0
	setcycle 7 S6 0
	setcycle 7 S7 0
	setcycle 7 S8 0
	setcycle 7 A1 8
	setcycle 7 A2 16
	setcycle 7 A3 9
	setcycle 7 A4 1
	setcycle 7 A5 5
	setcycle 7 A6 4
	setcycle 7 A7 10
	setcycle 7 A8 7
	setcycle 7 G1X -160
	setcycle 7 G1Y 0
	setcycle 7 G2X 160
	setcycle 7 G2Y 0
	setcycle 7 G3X -544
	setcycle 7 G3Y 256
	setcycle 7 G4X -544
	setcycle 7 G4Y 256
	setcycle 7 G5X -544
	setcycle 7 G5Y 256
	setcycle 7 G6X -544
	setcycle 7 G6Y 256
	setcycle 7 G7X -544
	setcycle 7 G7Y 256
	setcycle 7 G8X -544
	setcycle 7 G8Y 256
	setcycle 7 WAKTU 5000
	setcycle 8 correct_response 36
	setcycle 8 S1 6
	setcycle 8 S2 25
	setcycle 8 S3 0
	setcycle 8 S4 0
	setcycle 8 S5 0
	setcycle 8 S6 0
	setcycle 8 S7 0
	setcycle 8 S8 0
	setcycle 8 A1 13
	setcycle 8 A2 1
	setcycle 8 A3 6
	setcycle 8 A4 3
	setcycle 8 A5 8
	setcycle 8 A6 25
	setcycle 8 A7 7
	setcycle 8 A8 9
	setcycle 8 G1X -160
	setcycle 8 G1Y 0
	setcycle 8 G2X 160
	setcycle 8 G2Y 0
	setcycle 8 G3X -544
	setcycle 8 G3Y 256
	setcycle 8 G4X -544
	setcycle 8 G4Y 256
	setcycle 8 G5X -544
	setcycle 8 G5Y 256
	setcycle 8 G6X -544
	setcycle 8 G6Y 256
	setcycle 8 G7X -544
	setcycle 8 G7Y 256
	setcycle 8 G8X -544
	setcycle 8 G8Y 256
	setcycle 8 WAKTU 5000
	setcycle 9 correct_response 57
	setcycle 9 S1 14
	setcycle 9 S2 1
	setcycle 9 S3 0
	setcycle 9 S4 0
	setcycle 9 S5 0
	setcycle 9 S6 0
	setcycle 9 S7 0
	setcycle 9 S8 0
	setcycle 9 A1 7
	setcycle 9 A2 11
	setcycle 9 A3 3
	setcycle 9 A4 9
	setcycle 9 A5 14
	setcycle 9 A6 5
	setcycle 9 A7 1
	setcycle 9 A8 10
	setcycle 9 G1X -160
	setcycle 9 G1Y 0
	setcycle 9 G2X 160
	setcycle 9 G2Y 0
	setcycle 9 G3X -544
	setcycle 9 G3Y 256
	setcycle 9 G4X -544
	setcycle 9 G4Y 256
	setcycle 9 G5X -544
	setcycle 9 G5Y 256
	setcycle 9 G6X -544
	setcycle 9 G6Y 256
	setcycle 9 G7X -544
	setcycle 9 G7Y 256
	setcycle 9 G8X -544
	setcycle 9 G8Y 256
	setcycle 9 WAKTU 5000
	setcycle 10 correct_response 234
	setcycle 10 S1 19
	setcycle 10 S2 15
	setcycle 10 S3 27
	setcycle 10 S4 0
	setcycle 10 S5 0
	setcycle 10 S6 0
	setcycle 10 S7 0
	setcycle 10 S8 0
	setcycle 10 A1 1
	setcycle 10 A2 19
	setcycle 10 A3 15
	setcycle 10 A4 27
	setcycle 10 A5 8
	setcycle 10 A6 9
	setcycle 10 A7 10
	setcycle 10 A8 6
	setcycle 10 G1X -288
	setcycle 10 G1Y 0
	setcycle 10 G2X 0
	setcycle 10 G2Y 0
	setcycle 10 G3X 288
	setcycle 10 G3Y 0
	setcycle 10 G4X -544
	setcycle 10 G4Y 256
	setcycle 10 G5X -544
	setcycle 10 G5Y 256
	setcycle 10 G6X -544
	setcycle 10 G6Y 256
	setcycle 10 G7X -544
	setcycle 10 G7Y 256
	setcycle 10 G8X -544
	setcycle 10 G8Y 256
	setcycle 10 WAKTU 7500
	setcycle 11 correct_response 145
	setcycle 11 S1 5
	setcycle 11 S2 9
	setcycle 11 S3 28
	setcycle 11 S4 0
	setcycle 11 S5 0
	setcycle 11 S6 0
	setcycle 11 S7 0
	setcycle 11 S8 0
	setcycle 11 A1 5
	setcycle 11 A2 14
	setcycle 11 A3 6
	setcycle 11 A4 9
	setcycle 11 A5 28
	setcycle 11 A6 7
	setcycle 11 A7 3
	setcycle 11 A8 2
	setcycle 11 G1X -288
	setcycle 11 G1Y 0
	setcycle 11 G2X 0
	setcycle 11 G2Y 0
	setcycle 11 G3X 288
	setcycle 11 G3Y 0
	setcycle 11 G4X -544
	setcycle 11 G4Y 256
	setcycle 11 G5X -544
	setcycle 11 G5Y 256
	setcycle 11 G6X -544
	setcycle 11 G6Y 256
	setcycle 11 G7X -544
	setcycle 11 G7Y 256
	setcycle 11 G8X -544
	setcycle 11 G8Y 256
	setcycle 11 WAKTU 7500
	setcycle 12 correct_response 678
	setcycle 12 S1 21
	setcycle 12 S2 12
	setcycle 12 S3 6
	setcycle 12 S4 0
	setcycle 12 S5 0
	setcycle 12 S6 0
	setcycle 12 S7 0
	setcycle 12 S8 0
	setcycle 12 A1 9
	setcycle 12 A2 5
	setcycle 12 A3 4
	setcycle 12 A4 10
	setcycle 12 A5 11
	setcycle 12 A6 21
	setcycle 12 A7 12
	setcycle 12 A8 6
	setcycle 12 G1X -288
	setcycle 12 G1Y 0
	setcycle 12 G2X 0
	setcycle 12 G2Y 0
	setcycle 12 G3X 288
	setcycle 12 G3Y 0
	setcycle 12 G4X -544
	setcycle 12 G4Y 256
	setcycle 12 G5X -544
	setcycle 12 G5Y 256
	setcycle 12 G6X -544
	setcycle 12 G6Y 256
	setcycle 12 G7X -544
	setcycle 12 G7Y 256
	setcycle 12 G8X -544
	setcycle 12 G8Y 256
	setcycle 12 WAKTU 7500
	setcycle 13 correct_response 357
	setcycle 13 S1 19
	setcycle 13 S2 22
	setcycle 13 S3 12
	setcycle 13 S4 0
	setcycle 13 S5 0
	setcycle 13 S6 0
	setcycle 13 S7 0
	setcycle 13 S8 0
	setcycle 13 A1 7
	setcycle 13 A2 3
	setcycle 13 A3 19
	setcycle 13 A4 6
	setcycle 13 A5 22
	setcycle 13 A6 9
	setcycle 13 A7 12
	setcycle 13 A8 1
	setcycle 13 G1X -288
	setcycle 13 G1Y 0
	setcycle 13 G2X 0
	setcycle 13 G2Y 0
	setcycle 13 G3X 288
	setcycle 13 G3Y 0
	setcycle 13 G4X -544
	setcycle 13 G4Y 256
	setcycle 13 G5X -544
	setcycle 13 G5Y 256
	setcycle 13 G6X -544
	setcycle 13 G6Y 256
	setcycle 13 G7X -544
	setcycle 13 G7Y 256
	setcycle 13 G8X -544
	setcycle 13 G8Y 256
	setcycle 13 WAKTU 7500
	setcycle 14 correct_response 256
	setcycle 14 S1 18
	setcycle 14 S2 3
	setcycle 14 S3 24
	setcycle 14 S4 0
	setcycle 14 S5 0
	setcycle 14 S6 0
	setcycle 14 S7 0
	setcycle 14 S8 0
	setcycle 14 A1 10
	setcycle 14 A2 18
	setcycle 14 A3 7
	setcycle 14 A4 5
	setcycle 14 A5 3
	setcycle 14 A6 24
	setcycle 14 A7 1
	setcycle 14 A8 8
	setcycle 14 G1X -288
	setcycle 14 G1Y 0
	setcycle 14 G2X 0
	setcycle 14 G2Y 0
	setcycle 14 G3X 288
	setcycle 14 G3Y 0
	setcycle 14 G4X -544
	setcycle 14 G4Y 256
	setcycle 14 G5X -544
	setcycle 14 G5Y 256
	setcycle 14 G6X -544
	setcycle 14 G6Y 256
	setcycle 14 G7X -544
	setcycle 14 G7Y 256
	setcycle 14 G8X -544
	setcycle 14 G8Y 256
	setcycle 14 WAKTU 7500
	setcycle 15 correct_response 158
	setcycle 15 S1 30
	setcycle 15 S2 18
	setcycle 15 S3 11
	setcycle 15 S4 0
	setcycle 15 S5 0
	setcycle 15 S6 0
	setcycle 15 S7 0
	setcycle 15 S8 0
	setcycle 15 A1 30
	setcycle 15 A2 5
	setcycle 15 A3 8
	setcycle 15 A4 9
	setcycle 15 A5 18
	setcycle 15 A6 3
	setcycle 15 A7 2
	setcycle 15 A8 11
	setcycle 15 G1X -288
	setcycle 15 G1Y 0
	setcycle 15 G2X 0
	setcycle 15 G2Y 0
	setcycle 15 G3X 288
	setcycle 15 G3Y 0
	setcycle 15 G4X -544
	setcycle 15 G4Y 256
	setcycle 15 G5X -544
	setcycle 15 G5Y 256
	setcycle 15 G6X -544
	setcycle 15 G6Y 256
	setcycle 15 G7X -544
	setcycle 15 G7Y 256
	setcycle 15 G8X -544
	setcycle 15 G8Y 256
	setcycle 15 WAKTU 7500
	setcycle 16 correct_response 134
	setcycle 16 S1 17
	setcycle 16 S2 6
	setcycle 16 S3 7
	setcycle 16 S4 0
	setcycle 16 S5 0
	setcycle 16 S6 0
	setcycle 16 S7 0
	setcycle 16 S8 0
	setcycle 16 A1 17
	setcycle 16 A2 5
	setcycle 16 A3 6
	setcycle 16 A4 7
	setcycle 16 A5 8
	setcycle 16 A6 1
	setcycle 16 A7 2
	setcycle 16 A8 4
	setcycle 16 G1X -288
	setcycle 16 G1Y 0
	setcycle 16 G2X 0
	setcycle 16 G2Y 0
	setcycle 16 G3X 288
	setcycle 16 G3Y 0
	setcycle 16 G4X -544
	setcycle 16 G4Y 256
	setcycle 16 G5X -544
	setcycle 16 G5Y 256
	setcycle 16 G6X -544
	setcycle 16 G6Y 256
	setcycle 16 G7X -544
	setcycle 16 G7Y 256
	setcycle 16 G8X -544
	setcycle 16 G8Y 256
	setcycle 16 WAKTU 7500
	setcycle 17 correct_response 478
	setcycle 17 S1 7
	setcycle 17 S2 22
	setcycle 17 S3 25
	setcycle 17 S4 0
	setcycle 17 S5 0
	setcycle 17 S6 0
	setcycle 17 S7 0
	setcycle 17 S8 0
	setcycle 17 A1 14
	setcycle 17 A2 17
	setcycle 17 A3 9
	setcycle 17 A4 7
	setcycle 17 A5 6
	setcycle 17 A6 5
	setcycle 17 A7 22
	setcycle 17 A8 25
	setcycle 17 G1X -288
	setcycle 17 G1Y 0
	setcycle 17 G2X 0
	setcycle 17 G2Y 0
	setcycle 17 G3X 288
	setcycle 17 G3Y 0
	setcycle 17 G4X -544
	setcycle 17 G4Y 256
	setcycle 17 G5X -544
	setcycle 17 G5Y 256
	setcycle 17 G6X -544
	setcycle 17 G6Y 256
	setcycle 17 G7X -544
	setcycle 17 G7Y 256
	setcycle 17 G8X -544
	setcycle 17 G8Y 256
	setcycle 17 WAKTU 7500
	setcycle 18 correct_response 356
	setcycle 18 S1 21
	setcycle 18 S2 23
	setcycle 18 S3 14
	setcycle 18 S4 0
	setcycle 18 S5 0
	setcycle 18 S6 0
	setcycle 18 S7 0
	setcycle 18 S8 0
	setcycle 18 A1 11
	setcycle 18 A2 9
	setcycle 18 A3 21
	setcycle 18 A4 8
	setcycle 18 A5 23
	setcycle 18 A6 14
	setcycle 18 A7 20
	setcycle 18 A8 13
	setcycle 18 G1X -288
	setcycle 18 G1Y 0
	setcycle 18 G2X 0
	setcycle 18 G2Y 0
	setcycle 18 G3X 288
	setcycle 18 G3Y 0
	setcycle 18 G4X -544
	setcycle 18 G4Y 256
	setcycle 18 G5X -544
	setcycle 18 G5Y 256
	setcycle 18 G6X -544
	setcycle 18 G6Y 256
	setcycle 18 G7X -544
	setcycle 18 G7Y 256
	setcycle 18 G8X -544
	setcycle 18 G8Y 256
	setcycle 18 WAKTU 7500
	setcycle 19 correct_response 268
	setcycle 19 S1 13
	setcycle 19 S2 6
	setcycle 19 S3 27
	setcycle 19 S4 0
	setcycle 19 S5 0
	setcycle 19 S6 0
	setcycle 19 S7 0
	setcycle 19 S8 0
	setcycle 19 A1 7
	setcycle 19 A2 13
	setcycle 19 A3 9
	setcycle 19 A4 3
	setcycle 19 A5 1
	setcycle 19 A6 6
	setcycle 19 A7 11
	setcycle 19 A8 27
	setcycle 19 G1X -288
	setcycle 19 G1Y 0
	setcycle 19 G2X 0
	setcycle 19 G2Y 0
	setcycle 19 G3X 288
	setcycle 19 G3Y 0
	setcycle 19 G4X -544
	setcycle 19 G4Y 256
	setcycle 19 G5X -544
	setcycle 19 G5Y 256
	setcycle 19 G6X -544
	setcycle 19 G6Y 256
	setcycle 19 G7X -544
	setcycle 19 G7Y 256
	setcycle 19 G8X -544
	setcycle 19 G8Y 256
	setcycle 19 WAKTU 7500
	setcycle 20 correct_response 1234
	setcycle 20 S1 10
	setcycle 20 S2 5
	setcycle 20 S3 9
	setcycle 20 S4 7
	setcycle 20 S5 0
	setcycle 20 S6 0
	setcycle 20 S7 0
	setcycle 20 S8 0
	setcycle 20 A1 10
	setcycle 20 A2 5
	setcycle 20 A3 9
	setcycle 20 A4 7
	setcycle 20 A5 1
	setcycle 20 A6 2
	setcycle 20 A7 4
	setcycle 20 A8 6
	setcycle 20 G1X -384
	setcycle 20 G1Y 0
	setcycle 20 G2X -128
	setcycle 20 G2Y 0
	setcycle 20 G3X 128
	setcycle 20 G3Y 0
	setcycle 20 G4X 384
	setcycle 20 G4Y 0
	setcycle 20 G5X -544
	setcycle 20 G5Y 256
	setcycle 20 G6X -544
	setcycle 20 G6Y 256
	setcycle 20 G7X -544
	setcycle 20 G7Y 256
	setcycle 20 G8X -544
	setcycle 20 G8Y 256
	setcycle 20 WAKTU 10000
	setcycle 21 correct_response 2457
	setcycle 21 S1 9
	setcycle 21 S2 27
	setcycle 21 S3 20
	setcycle 21 S4 28
	setcycle 21 S5 0
	setcycle 21 S6 0
	setcycle 21 S7 0
	setcycle 21 S8 0
	setcycle 21 A1 21
	setcycle 21 A2 9
	setcycle 21 A3 4
	setcycle 21 A4 27
	setcycle 21 A5 20
	setcycle 21 A6 11
	setcycle 21 A7 28
	setcycle 21 A8 3
	setcycle 21 G1X -384
	setcycle 21 G1Y 0
	setcycle 21 G2X -128
	setcycle 21 G2Y 0
	setcycle 21 G3X 128
	setcycle 21 G3Y 0
	setcycle 21 G4X 384
	setcycle 21 G4Y 0
	setcycle 21 G5X -544
	setcycle 21 G5Y 256
	setcycle 21 G6X -544
	setcycle 21 G6Y 256
	setcycle 21 G7X -544
	setcycle 21 G7Y 256
	setcycle 21 G8X -544
	setcycle 21 G8Y 256
	setcycle 21 WAKTU 10000
	setcycle 22 correct_response 1456
	setcycle 22 S1 10
	setcycle 22 S2 23
	setcycle 22 S3 11
	setcycle 22 S4 9
	setcycle 22 S5 0
	setcycle 22 S6 0
	setcycle 22 S7 0
	setcycle 22 S8 0
	setcycle 22 A1 10
	setcycle 22 A2 1
	setcycle 22 A3 2
	setcycle 22 A4 23
	setcycle 22 A5 11
	setcycle 22 A6 9
	setcycle 22 A7 8
	setcycle 22 A8 3
	setcycle 22 G1X -384
	setcycle 22 G1Y 0
	setcycle 22 G2X -128
	setcycle 22 G2Y 0
	setcycle 22 G3X 128
	setcycle 22 G3Y 0
	setcycle 22 G4X 384
	setcycle 22 G4Y 0
	setcycle 22 G5X -544
	setcycle 22 G5Y 256
	setcycle 22 G6X -544
	setcycle 22 G6Y 256
	setcycle 22 G7X -544
	setcycle 22 G7Y 256
	setcycle 22 G8X -544
	setcycle 22 G8Y 256
	setcycle 22 WAKTU 10000
	setcycle 23 correct_response 3568
	setcycle 23 S1 23
	setcycle 23 S2 12
	setcycle 23 S3 18
	setcycle 23 S4 1
	setcycle 23 S5 0
	setcycle 23 S6 0
	setcycle 23 S7 0
	setcycle 23 S8 0
	setcycle 23 A1 18
	setcycle 23 A2 17
	setcycle 23 A3 23
	setcycle 23 A4 22
	setcycle 23 A5 12
	setcycle 23 A6 18
	setcycle 23 A7 26
	setcycle 23 A8 1
	setcycle 23 G1X -384
	setcycle 23 G1Y 0
	setcycle 23 G2X -128
	setcycle 23 G2Y 0
	setcycle 23 G3X 128
	setcycle 23 G3Y 0
	setcycle 23 G4X 384
	setcycle 23 G4Y 0
	setcycle 23 G5X -544
	setcycle 23 G5Y 256
	setcycle 23 G6X -544
	setcycle 23 G6Y 256
	setcycle 23 G7X -544
	setcycle 23 G7Y 256
	setcycle 23 G8X -544
	setcycle 23 G8Y 256
	setcycle 23 WAKTU 10000
	setcycle 24 correct_response 4567
	setcycle 24 S1 12
	setcycle 24 S2 13
	setcycle 24 S3 25
	setcycle 24 S4 20
	setcycle 24 S5 0
	setcycle 24 S6 0
	setcycle 24 S7 0
	setcycle 24 S8 0
	setcycle 24 A1 14
	setcycle 24 A2 4
	setcycle 24 A3 5
	setcycle 24 A4 12
	setcycle 24 A5 13
	setcycle 24 A6 25
	setcycle 24 A7 20
	setcycle 24 A8 7
	setcycle 24 G1X -384
	setcycle 24 G1Y 0
	setcycle 24 G2X -128
	setcycle 24 G2Y 0
	setcycle 24 G3X 128
	setcycle 24 G3Y 0
	setcycle 24 G4X 384
	setcycle 24 G4Y 0
	setcycle 24 G5X -544
	setcycle 24 G5Y 256
	setcycle 24 G6X -544
	setcycle 24 G6Y 256
	setcycle 24 G7X -544
	setcycle 24 G7Y 256
	setcycle 24 G8X -544
	setcycle 24 G8Y 256
	setcycle 24 WAKTU 10000
	setcycle 25 correct_response 2467
	setcycle 25 S1 28
	setcycle 25 S2 8
	setcycle 25 S3 11
	setcycle 25 S4 24
	setcycle 25 S5 0
	setcycle 25 S6 0
	setcycle 25 S7 0
	setcycle 25 S8 0
	setcycle 25 A1 1
	setcycle 25 A2 28
	setcycle 25 A3 6
	setcycle 25 A4 8
	setcycle 25 A5 21
	setcycle 25 A6 11
	setcycle 25 A7 24
	setcycle 25 A8 15
	setcycle 25 G1X -384
	setcycle 25 G1Y 0
	setcycle 25 G2X -128
	setcycle 25 G2Y 0
	setcycle 25 G3X 128
	setcycle 25 G3Y 0
	setcycle 25 G4X 384
	setcycle 25 G4Y 0
	setcycle 25 G5X -544
	setcycle 25 G5Y 256
	setcycle 25 G6X -544
	setcycle 25 G6Y 256
	setcycle 25 G7X -544
	setcycle 25 G7Y 256
	setcycle 25 G8X -544
	setcycle 25 G8Y 256
	setcycle 25 WAKTU 10000
	setcycle 26 correct_response 2378
	setcycle 26 S1 29
	setcycle 26 S2 27
	setcycle 26 S3 17
	setcycle 26 S4 20
	setcycle 26 S5 0
	setcycle 26 S6 0
	setcycle 26 S7 0
	setcycle 26 S8 0
	setcycle 26 A1 18
	setcycle 26 A2 29
	setcycle 26 A3 27
	setcycle 26 A4 24
	setcycle 26 A5 13
	setcycle 26 A6 6
	setcycle 26 A7 17
	setcycle 26 A8 20
	setcycle 26 G1X -384
	setcycle 26 G1Y 0
	setcycle 26 G2X -128
	setcycle 26 G2Y 0
	setcycle 26 G3X 128
	setcycle 26 G3Y 0
	setcycle 26 G4X 384
	setcycle 26 G4Y 0
	setcycle 26 G5X -544
	setcycle 26 G5Y 256
	setcycle 26 G6X -544
	setcycle 26 G6Y 256
	setcycle 26 G7X -544
	setcycle 26 G7Y 256
	setcycle 26 G8X -544
	setcycle 26 G8Y 256
	setcycle 26 WAKTU 10000
	setcycle 27 correct_response 3568
	setcycle 27 S1 4
	setcycle 27 S2 14
	setcycle 27 S3 7
	setcycle 27 S4 21
	setcycle 27 S5 0
	setcycle 27 S6 0
	setcycle 27 S7 0
	setcycle 27 S8 0
	setcycle 27 A1 2
	setcycle 27 A2 8
	setcycle 27 A3 4
	setcycle 27 A4 3
	setcycle 27 A5 14
	setcycle 27 A6 7
	setcycle 27 A7 11
	setcycle 27 A8 21
	setcycle 27 G1X -384
	setcycle 27 G1Y 0
	setcycle 27 G2X -128
	setcycle 27 G2Y 0
	setcycle 27 G3X 128
	setcycle 27 G3Y 0
	setcycle 27 G4X 384
	setcycle 27 G4Y 0
	setcycle 27 G5X -544
	setcycle 27 G5Y 256
	setcycle 27 G6X -544
	setcycle 27 G6Y 256
	setcycle 27 G7X -544
	setcycle 27 G7Y 256
	setcycle 27 G8X -544
	setcycle 27 G8Y 256
	setcycle 27 WAKTU 10000
	setcycle 28 correct_response 1578
	setcycle 28 S1 30
	setcycle 28 S2 2
	setcycle 28 S3 13
	setcycle 28 S4 20
	setcycle 28 S5 0
	setcycle 28 S6 0
	setcycle 28 S7 0
	setcycle 28 S8 0
	setcycle 28 A1 30
	setcycle 28 A2 1
	setcycle 28 A3 8
	setcycle 28 A4 15
	setcycle 28 A5 2
	setcycle 28 A6 4
	setcycle 28 A7 13
	setcycle 28 A8 20
	setcycle 28 G1X -384
	setcycle 28 G1Y 0
	setcycle 28 G2X -128
	setcycle 28 G2Y 0
	setcycle 28 G3X 128
	setcycle 28 G3Y 0
	setcycle 28 G4X 384
	setcycle 28 G4Y 0
	setcycle 28 G5X -544
	setcycle 28 G5Y 256
	setcycle 28 G6X -544
	setcycle 28 G6Y 256
	setcycle 28 G7X -544
	setcycle 28 G7Y 256
	setcycle 28 G8X -544
	setcycle 28 G8Y 256
	setcycle 28 WAKTU 10000
	setcycle 29 correct_response 2356
	setcycle 29 S1 26
	setcycle 29 S2 5
	setcycle 29 S3 21
	setcycle 29 S4 1
	setcycle 29 S5 0
	setcycle 29 S6 0
	setcycle 29 S7 0
	setcycle 29 S8 0
	setcycle 29 A1 9
	setcycle 29 A2 26
	setcycle 29 A3 5
	setcycle 29 A4 13
	setcycle 29 A5 21
	setcycle 29 A6 1
	setcycle 29 A7 6
	setcycle 29 A8 10
	setcycle 29 G1X -384
	setcycle 29 G1Y 0
	setcycle 29 G2X -128
	setcycle 29 G2Y 0
	setcycle 29 G3X 128
	setcycle 29 G3Y 0
	setcycle 29 G4X 384
	setcycle 29 G4Y 0
	setcycle 29 G5X -544
	setcycle 29 G5Y 256
	setcycle 29 G6X -544
	setcycle 29 G6Y 256
	setcycle 29 G7X -544
	setcycle 29 G7Y 256
	setcycle 29 G8X -544
	setcycle 29 G8Y 256
	setcycle 29 WAKTU 10000
	setcycle 30 correct_response 12458
	setcycle 30 S1 3
	setcycle 30 S2 28
	setcycle 30 S3 20
	setcycle 30 S4 19
	setcycle 30 S5 7
	setcycle 30 S6 0
	setcycle 30 S7 0
	setcycle 30 S8 0
	setcycle 30 A1 3
	setcycle 30 A2 28
	setcycle 30 A3 1
	setcycle 30 A4 20
	setcycle 30 A5 19
	setcycle 30 A6 5
	setcycle 30 A7 8
	setcycle 30 A8 7
	setcycle 30 G1X -448
	setcycle 30 G1Y 0
	setcycle 30 G2X -224
	setcycle 30 G2Y 0
	setcycle 30 G3X 0
	setcycle 30 G3Y 0
	setcycle 30 G4X 224
	setcycle 30 G4Y 0
	setcycle 30 G5X 448
	setcycle 30 G5Y 0
	setcycle 30 G6X -544
	setcycle 30 G6Y 256
	setcycle 30 G7X -544
	setcycle 30 G7Y 256
	setcycle 30 G8X -544
	setcycle 30 G8Y 256
	setcycle 30 WAKTU 12500
	setcycle 31 correct_response 23678
	setcycle 31 S1 7
	setcycle 31 S2 5
	setcycle 31 S3 17
	setcycle 31 S4 22
	setcycle 31 S5 11
	setcycle 31 S6 0
	setcycle 31 S7 0
	setcycle 31 S8 0
	setcycle 31 A1 12
	setcycle 31 A2 7
	setcycle 31 A3 5
	setcycle 31 A4 6
	setcycle 31 A5 2
	setcycle 31 A6 17
	setcycle 31 A7 22
	setcycle 31 A8 11
	setcycle 31 G1X -448
	setcycle 31 G1Y 0
	setcycle 31 G2X -224
	setcycle 31 G2Y 0
	setcycle 31 G3X 0
	setcycle 31 G3Y 0
	setcycle 31 G4X 224
	setcycle 31 G4Y 0
	setcycle 31 G5X 448
	setcycle 31 G5Y 0
	setcycle 31 G6X -544
	setcycle 31 G6Y 256
	setcycle 31 G7X -544
	setcycle 31 G7Y 256
	setcycle 31 G8X -544
	setcycle 31 G8Y 256
	setcycle 31 WAKTU 12500
	setcycle 32 correct_response 23456
	setcycle 32 S1 9
	setcycle 32 S2 15
	setcycle 32 S3 18
	setcycle 32 S4 10
	setcycle 32 S5 26
	setcycle 32 S6 0
	setcycle 32 S7 0
	setcycle 32 S8 0
	setcycle 32 A1 6
	setcycle 32 A2 9
	setcycle 32 A3 15
	setcycle 32 A4 18
	setcycle 32 A5 10
	setcycle 32 A6 26
	setcycle 32 A7 8
	setcycle 32 A8 7
	setcycle 32 G1X -448
	setcycle 32 G1Y 0
	setcycle 32 G2X -224
	setcycle 32 G2Y 0
	setcycle 32 G3X 0
	setcycle 32 G3Y 0
	setcycle 32 G4X 224
	setcycle 32 G4Y 0
	setcycle 32 G5X 448
	setcycle 32 G5Y 0
	setcycle 32 G6X -544
	setcycle 32 G6Y 256
	setcycle 32 G7X -544
	setcycle 32 G7Y 256
	setcycle 32 G8X -544
	setcycle 32 G8Y 256
	setcycle 32 WAKTU 12500
	setcycle 33 correct_response 45678
	setcycle 33 S1 12
	setcycle 33 S2 29
	setcycle 33 S3 30
	setcycle 33 S4 20
	setcycle 33 S5 19
	setcycle 33 S6 0
	setcycle 33 S7 0
	setcycle 33 S8 0
	setcycle 33 A1 3
	setcycle 33 A2 11
	setcycle 33 A3 6
	setcycle 33 A4 12
	setcycle 33 A5 29
	setcycle 33 A6 30
	setcycle 33 A7 20
	setcycle 33 A8 19
	setcycle 33 G1X -448
	setcycle 33 G1Y 0
	setcycle 33 G2X -224
	setcycle 33 G2Y 0
	setcycle 33 G3X 0
	setcycle 33 G3Y 0
	setcycle 33 G4X 224
	setcycle 33 G4Y 0
	setcycle 33 G5X 448
	setcycle 33 G5Y 0
	setcycle 33 G6X -544
	setcycle 33 G6Y 256
	setcycle 33 G7X -544
	setcycle 33 G7Y 256
	setcycle 33 G8X -544
	setcycle 33 G8Y 256
	setcycle 33 WAKTU 12500
	setcycle 34 correct_response 34567
	setcycle 34 S1 6
	setcycle 34 S2 25
	setcycle 34 S3 15
	setcycle 34 S4 24
	setcycle 34 S5 18
	setcycle 34 S6 0
	setcycle 34 S7 0
	setcycle 34 S8 0
	setcycle 34 A1 4
	setcycle 34 A2 7
	setcycle 34 A3 6
	setcycle 34 A4 25
	setcycle 34 A5 15
	setcycle 34 A6 24
	setcycle 34 A7 18
	setcycle 34 A8 12
	setcycle 34 G1X -448
	setcycle 34 G1Y 0
	setcycle 34 G2X -224
	setcycle 34 G2Y 0
	setcycle 34 G3X 0
	setcycle 34 G3Y 0
	setcycle 34 G4X 224
	setcycle 34 G4Y 0
	setcycle 34 G5X 448
	setcycle 34 G5Y 0
	setcycle 34 G6X -544
	setcycle 34 G6Y 256
	setcycle 34 G7X -544
	setcycle 34 G7Y 256
	setcycle 34 G8X -544
	setcycle 34 G8Y 256
	setcycle 34 WAKTU 12500
	setcycle 35 correct_response 13467
	setcycle 35 S1 9
	setcycle 35 S2 18
	setcycle 35 S3 28
	setcycle 35 S4 17
	setcycle 35 S5 8
	setcycle 35 S6 0
	setcycle 35 S7 0
	setcycle 35 S8 0
	setcycle 35 A1 9
	setcycle 35 A2 12
	setcycle 35 A3 18
	setcycle 35 A4 28
	setcycle 35 A5 7
	setcycle 35 A6 17
	setcycle 35 A7 8
	setcycle 35 A8 5
	setcycle 35 G1X -448
	setcycle 35 G1Y 0
	setcycle 35 G2X -224
	setcycle 35 G2Y 0
	setcycle 35 G3X 0
	setcycle 35 G3Y 0
	setcycle 35 G4X 224
	setcycle 35 G4Y 0
	setcycle 35 G5X 448
	setcycle 35 G5Y 0
	setcycle 35 G6X -544
	setcycle 35 G6Y 256
	setcycle 35 G7X -544
	setcycle 35 G7Y 256
	setcycle 35 G8X -544
	setcycle 35 G8Y 256
	setcycle 35 WAKTU 12500
	setcycle 36 correct_response 34567
	setcycle 36 S1 18
	setcycle 36 S2 10
	setcycle 36 S3 11
	setcycle 36 S4 14
	setcycle 36 S5 20
	setcycle 36 S6 0
	setcycle 36 S7 0
	setcycle 36 S8 0
	setcycle 36 A1 3
	setcycle 36 A2 5
	setcycle 36 A3 18
	setcycle 36 A4 10
	setcycle 36 A5 11
	setcycle 36 A6 14
	setcycle 36 A7 20
	setcycle 36 A8 12
	setcycle 36 G1X -448
	setcycle 36 G1Y 0
	setcycle 36 G2X -224
	setcycle 36 G2Y 0
	setcycle 36 G3X 0
	setcycle 36 G3Y 0
	setcycle 36 G4X 224
	setcycle 36 G4Y 0
	setcycle 36 G5X 448
	setcycle 36 G5Y 0
	setcycle 36 G6X -544
	setcycle 36 G6Y 256
	setcycle 36 G7X -544
	setcycle 36 G7Y 256
	setcycle 36 G8X -544
	setcycle 36 G8Y 256
	setcycle 36 WAKTU 12500
	setcycle 37 correct_response 12346
	setcycle 37 S1 27
	setcycle 37 S2 2
	setcycle 37 S3 28
	setcycle 37 S4 23
	setcycle 37 S5 8
	setcycle 37 S6 0
	setcycle 37 S7 0
	setcycle 37 S8 0
	setcycle 37 A1 27
	setcycle 37 A2 2
	setcycle 37 A3 28
	setcycle 37 A4 23
	setcycle 37 A5 7
	setcycle 37 A6 8
	setcycle 37 A7 9
	setcycle 37 A8 11
	setcycle 37 G1X -448
	setcycle 37 G1Y 0
	setcycle 37 G2X -224
	setcycle 37 G2Y 0
	setcycle 37 G3X 0
	setcycle 37 G3Y 0
	setcycle 37 G4X 224
	setcycle 37 G4Y 0
	setcycle 37 G5X 448
	setcycle 37 G5Y 0
	setcycle 37 G6X -544
	setcycle 37 G6Y 256
	setcycle 37 G7X -544
	setcycle 37 G7Y 256
	setcycle 37 G8X -544
	setcycle 37 G8Y 256
	setcycle 37 WAKTU 12500
	setcycle 38 correct_response 24567
	setcycle 38 S1 10
	setcycle 38 S2 7
	setcycle 38 S3 26
	setcycle 38 S4 20
	setcycle 38 S5 24
	setcycle 38 S6 0
	setcycle 38 S7 0
	setcycle 38 S8 0
	setcycle 38 A1 4
	setcycle 38 A2 10
	setcycle 38 A3 9
	setcycle 38 A4 7
	setcycle 38 A5 26
	setcycle 38 A6 20
	setcycle 38 A7 24
	setcycle 38 A8 8
	setcycle 38 G1X -448
	setcycle 38 G1Y 0
	setcycle 38 G2X -224
	setcycle 38 G2Y 0
	setcycle 38 G3X 0
	setcycle 38 G3Y 0
	setcycle 38 G4X 224
	setcycle 38 G4Y 0
	setcycle 38 G5X 448
	setcycle 38 G5Y 0
	setcycle 38 G6X -544
	setcycle 38 G6Y 256
	setcycle 38 G7X -544
	setcycle 38 G7Y 256
	setcycle 38 G8X -544
	setcycle 38 G8Y 256
	setcycle 38 WAKTU 12500
	setcycle 39 correct_response 13456
	setcycle 39 S1 7
	setcycle 39 S2 8
	setcycle 39 S3 21
	setcycle 39 S4 2
	setcycle 39 S5 17
	setcycle 39 S6 0
	setcycle 39 S7 0
	setcycle 39 S8 0
	setcycle 39 A1 7
	setcycle 39 A2 14
	setcycle 39 A3 8
	setcycle 39 A4 21
	setcycle 39 A5 2
	setcycle 39 A6 17
	setcycle 39 A7 12
	setcycle 39 A8 4
	setcycle 39 G1X -448
	setcycle 39 G1Y 0
	setcycle 39 G2X -224
	setcycle 39 G2Y 0
	setcycle 39 G3X 0
	setcycle 39 G3Y 0
	setcycle 39 G4X 224
	setcycle 39 G4Y 0
	setcycle 39 G5X 448
	setcycle 39 G5Y 0
	setcycle 39 G6X -544
	setcycle 39 G6Y 256
	setcycle 39 G7X -544
	setcycle 39 G7Y 256
	setcycle 39 G8X -544
	setcycle 39 G8Y 256
	setcycle 39 WAKTU 12500
	setcycle 40 correct_response 124567
	setcycle 40 S1 17
	setcycle 40 S2 10
	setcycle 40 S3 19
	setcycle 40 S4 11
	setcycle 40 S5 29
	setcycle 40 S6 7
	setcycle 40 S7 0
	setcycle 40 S8 0
	setcycle 40 A1 17
	setcycle 40 A2 10
	setcycle 40 A3 5
	setcycle 40 A4 19
	setcycle 40 A5 11
	setcycle 40 A6 29
	setcycle 40 A7 7
	setcycle 40 A8 6
	setcycle 40 G1X -256
	setcycle 40 G1Y -160
	setcycle 40 G2X 0
	setcycle 40 G2Y -160
	setcycle 40 G3X 256
	setcycle 40 G3Y -160
	setcycle 40 G4X -256
	setcycle 40 G4Y 160
	setcycle 40 G5X 0
	setcycle 40 G5Y 160
	setcycle 40 G6X 256
	setcycle 40 G6Y 160
	setcycle 40 G7X -544
	setcycle 40 G7Y 256
	setcycle 40 G8X -544
	setcycle 40 G8Y 256
	setcycle 40 WAKTU 15000
	setcycle 41 correct_response 234568
	setcycle 41 S1 15
	setcycle 41 S2 29
	setcycle 41 S3 12
	setcycle 41 S4 3
	setcycle 41 S5 26
	setcycle 41 S6 16
	setcycle 41 S7 0
	setcycle 41 S8 0
	setcycle 41 A1 1
	setcycle 41 A2 15
	setcycle 41 A3 29
	setcycle 41 A4 12
	setcycle 41 A5 3
	setcycle 41 A6 26
	setcycle 41 A7 14
	setcycle 41 A8 16
	setcycle 41 G1X -256
	setcycle 41 G1Y -160
	setcycle 41 G2X 0
	setcycle 41 G2Y -160
	setcycle 41 G3X 256
	setcycle 41 G3Y -160
	setcycle 41 G4X -256
	setcycle 41 G4Y 160
	setcycle 41 G5X 0
	setcycle 41 G5Y 160
	setcycle 41 G6X 256
	setcycle 41 G6Y 160
	setcycle 41 G7X -544
	setcycle 41 G7Y 256
	setcycle 41 G8X -544
	setcycle 41 G8Y 256
	setcycle 41 WAKTU 15000
	setcycle 42 correct_response 135678
	setcycle 42 S1 21
	setcycle 42 S2 3
	setcycle 42 S3 14
	setcycle 42 S4 2
	setcycle 42 S5 13
	setcycle 42 S6 10
	setcycle 42 S7 0
	setcycle 42 S8 0
	setcycle 42 A1 21
	setcycle 42 A2 4
	setcycle 42 A3 3
	setcycle 42 A4 5
	setcycle 42 A5 14
	setcycle 42 A6 2
	setcycle 42 A7 13
	setcycle 42 A8 10
	setcycle 42 G1X -256
	setcycle 42 G1Y -160
	setcycle 42 G2X 0
	setcycle 42 G2Y -160
	setcycle 42 G3X 256
	setcycle 42 G3Y -160
	setcycle 42 G4X -256
	setcycle 42 G4Y 160
	setcycle 42 G5X 0
	setcycle 42 G5Y 160
	setcycle 42 G6X 256
	setcycle 42 G6Y 160
	setcycle 42 G7X -544
	setcycle 42 G7Y 256
	setcycle 42 G8X -544
	setcycle 42 G8Y 256
	setcycle 42 WAKTU 15000
	setcycle 43 correct_response 123456
	setcycle 43 S1 1
	setcycle 43 S2 23
	setcycle 43 S3 10
	setcycle 43 S4 9
	setcycle 43 S5 21
	setcycle 43 S6 27
	setcycle 43 S7 0
	setcycle 43 S8 0
	setcycle 43 A1 1
	setcycle 43 A2 23
	setcycle 43 A3 10
	setcycle 43 A4 9
	setcycle 43 A5 21
	setcycle 43 A6 27
	setcycle 43 A7 6
	setcycle 43 A8 12
	setcycle 43 G1X -256
	setcycle 43 G1Y -160
	setcycle 43 G2X 0
	setcycle 43 G2Y -160
	setcycle 43 G3X 256
	setcycle 43 G3Y -160
	setcycle 43 G4X -256
	setcycle 43 G4Y 160
	setcycle 43 G5X 0
	setcycle 43 G5Y 160
	setcycle 43 G6X 256
	setcycle 43 G6Y 160
	setcycle 43 G7X -544
	setcycle 43 G7Y 256
	setcycle 43 G8X -544
	setcycle 43 G8Y 256
	setcycle 43 WAKTU 15000
	setcycle 44 correct_response 345678
	setcycle 44 S1 29
	setcycle 44 S2 9
	setcycle 44 S3 7
	setcycle 44 S4 8
	setcycle 44 S5 21
	setcycle 44 S6 28
	setcycle 44 S7 0
	setcycle 44 S8 0
	setcycle 44 A1 10
	setcycle 44 A2 11
	setcycle 44 A3 29
	setcycle 44 A4 9
	setcycle 44 A5 7
	setcycle 44 A6 8
	setcycle 44 A7 21
	setcycle 44 A8 28
	setcycle 44 G1X -256
	setcycle 44 G1Y -160
	setcycle 44 G2X 0
	setcycle 44 G2Y -160
	setcycle 44 G3X 256
	setcycle 44 G3Y -160
	setcycle 44 G4X -256
	setcycle 44 G4Y 160
	setcycle 44 G5X 0
	setcycle 44 G5Y 160
	setcycle 44 G6X 256
	setcycle 44 G6Y 160
	setcycle 44 G7X -544
	setcycle 44 G7Y 256
	setcycle 44 G8X -544
	setcycle 44 G8Y 256
	setcycle 44 WAKTU 15000
	setcycle 45 correct_response 245678
	setcycle 45 S1 5
	setcycle 45 S2 16
	setcycle 45 S3 2
	setcycle 45 S4 24
	setcycle 45 S5 10
	setcycle 45 S6 1
	setcycle 45 S7 0
	setcycle 45 S8 0
	setcycle 45 A1 9
	setcycle 45 A2 5
	setcycle 45 A3 3
	setcycle 45 A4 16
	setcycle 45 A5 2
	setcycle 45 A6 24
	setcycle 45 A7 10
	setcycle 45 A8 1
	setcycle 45 G1X -256
	setcycle 45 G1Y -160
	setcycle 45 G2X 0
	setcycle 45 G2Y -160
	setcycle 45 G3X 256
	setcycle 45 G3Y -160
	setcycle 45 G4X -256
	setcycle 45 G4Y 160
	setcycle 45 G5X 0
	setcycle 45 G5Y 160
	setcycle 45 G6X 256
	setcycle 45 G6Y 160
	setcycle 45 G7X -544
	setcycle 45 G7Y 256
	setcycle 45 G8X -544
	setcycle 45 G8Y 256
	setcycle 45 WAKTU 15000
	setcycle 46 correct_response 134678
	setcycle 46 S1 12
	setcycle 46 S2 19
	setcycle 46 S3 18
	setcycle 46 S4 28
	setcycle 46 S5 6
	setcycle 46 S6 30
	setcycle 46 S7 0
	setcycle 46 S8 0
	setcycle 46 A1 12
	setcycle 46 A2 5
	setcycle 46 A3 19
	setcycle 46 A4 18
	setcycle 46 A5 16
	setcycle 46 A6 28
	setcycle 46 A7 6
	setcycle 46 A8 30
	setcycle 46 G1X -256
	setcycle 46 G1Y -160
	setcycle 46 G2X 0
	setcycle 46 G2Y -160
	setcycle 46 G3X 256
	setcycle 46 G3Y -160
	setcycle 46 G4X -256
	setcycle 46 G4Y 160
	setcycle 46 G5X 0
	setcycle 46 G5Y 160
	setcycle 46 G6X 256
	setcycle 46 G6Y 160
	setcycle 46 G7X -544
	setcycle 46 G7Y 256
	setcycle 46 G8X -544
	setcycle 46 G8Y 256
	setcycle 46 WAKTU 15000
	setcycle 47 correct_response 123468
	setcycle 47 S1 3
	setcycle 47 S2 30
	setcycle 47 S3 27
	setcycle 47 S4 23
	setcycle 47 S5 17
	setcycle 47 S6 28
	setcycle 47 S7 0
	setcycle 47 S8 0
	setcycle 47 A1 3
	setcycle 47 A2 30
	setcycle 47 A3 27
	setcycle 47 A4 23
	setcycle 47 A5 1
	setcycle 47 A6 17
	setcycle 47 A7 9
	setcycle 47 A8 28
	setcycle 47 G1X -256
	setcycle 47 G1Y -160
	setcycle 47 G2X 0
	setcycle 47 G2Y -160
	setcycle 47 G3X 256
	setcycle 47 G3Y -160
	setcycle 47 G4X -256
	setcycle 47 G4Y 160
	setcycle 47 G5X 0
	setcycle 47 G5Y 160
	setcycle 47 G6X 256
	setcycle 47 G6Y 160
	setcycle 47 G7X -544
	setcycle 47 G7Y 256
	setcycle 47 G8X -544
	setcycle 47 G8Y 256
	setcycle 47 WAKTU 15000
	setcycle 48 correct_response 345678
	setcycle 48 S1 29
	setcycle 48 S2 28
	setcycle 48 S3 30
	setcycle 48 S4 15
	setcycle 48 S5 6
	setcycle 48 S6 20
	setcycle 48 S7 0
	setcycle 48 S8 0
	setcycle 48 A1 5
	setcycle 48 A2 18
	setcycle 48 A3 29
	setcycle 48 A4 28
	setcycle 48 A5 30
	setcycle 48 A6 15
	setcycle 48 A7 6
	setcycle 48 A8 20
	setcycle 48 G1X -256
	setcycle 48 G1Y -160
	setcycle 48 G2X 0
	setcycle 48 G2Y -160
	setcycle 48 G3X 256
	setcycle 48 G3Y -160
	setcycle 48 G4X -256
	setcycle 48 G4Y 160
	setcycle 48 G5X 0
	setcycle 48 G5Y 160
	setcycle 48 G6X 256
	setcycle 48 G6Y 160
	setcycle 48 G7X -544
	setcycle 48 G7Y 256
	setcycle 48 G8X -544
	setcycle 48 G8Y 256
	setcycle 48 WAKTU 15000
	setcycle 49 correct_response 124567
	setcycle 49 S1 7
	setcycle 49 S2 11
	setcycle 49 S3 4
	setcycle 49 S4 21
	setcycle 49 S5 24
	setcycle 49 S6 28
	setcycle 49 S7 0
	setcycle 49 S8 0
	setcycle 49 A1 7
	setcycle 49 A2 11
	setcycle 49 A3 10
	setcycle 49 A4 4
	setcycle 49 A5 21
	setcycle 49 A6 24
	setcycle 49 A7 28
	setcycle 49 A8 2
	setcycle 49 G1X -256
	setcycle 49 G1Y -160
	setcycle 49 G2X 0
	setcycle 49 G2Y -160
	setcycle 49 G3X 256
	setcycle 49 G3Y -160
	setcycle 49 G4X -256
	setcycle 49 G4Y 160
	setcycle 49 G5X 0
	setcycle 49 G5Y 160
	setcycle 49 G6X 256
	setcycle 49 G6Y 160
	setcycle 49 G7X -544
	setcycle 49 G7Y 256
	setcycle 49 G8X -544
	setcycle 49 G8Y 256
	setcycle 49 WAKTU 15000
	run seq_capacity

define sketchpad benar
	set duration 250
	set description "Displays stimuli"
	draw textline center=1 color=black font_bold=yes font_family=arabic font_italic=no font_size=25 html=yes show_if=always text="Hebat!" x=0 y=160 z_index=0
	draw image center=1 file="corect.png" scale=0.30000000000000016 show_if=always x=0 y=0 z_index=0

define feedback feedback_capacity
	set reset_variables yes
	set duration keypress
	set description "Provides feedback to the participant"
	draw textline center=1 color="#000000" font_bold=yes font_family=serif font_italic=no font_size=35 html=yes show_if=always text="Skor Anda : <br />[total]/50<br />" x=0 y=32 z_index=0
	draw textline center=1 color=black font_bold=no font_family=serif font_italic=no font_size=26 html=yes show_if=always text="Selamat!" x=0 y=-64 z_index=0

define sketchpad fixation
	set duration 250
	set description "Displays stimuli"
	draw image center=1 file="target.png" scale=0.40000000000000013 show_if=always x=0 y=-96 z_index=0

define form_base form_capacity
	set timeout 50000
	set spacing 10
	set rows "1;1;1;1"
	set only_render no
	set margins "50;50;50;50"
	set description "A generic form plug-in"
	set cols "1;1;1;1;1;1;1;1"
	set _theme gray
	widget 0 0 1 1 image path="[A1].png"
	widget 1 0 1 1 image path="[A2].png"
	widget 2 0 1 1 image path="[A3].png"
	widget 3 0 1 1 image path="[A4].png"
	widget 4 0 1 1 image path="[A5].png"
	widget 5 0 1 1 image path="[A6].png"
	widget 6 0 1 1 image path="[A7].png"
	widget 7 0 1 1 image path="[A8].png"
	widget 1 1 6 1 label text="Ketik angka gambar yang muncul!"
	widget 1 2 6 1 text_input center=yes frame=yes return_accepts=yes stub="Ketik disini …" text="" var=response
	widget 1 3 6 1 button text=Selanjutnya
	widget 0 0 1 2 label text=1
	widget 1 0 1 2 label text=2
	widget 2 0 1 2 label text=3
	widget 3 0 1 2 label text=4
	widget 4 0 1 2 label text=5
	widget 5 0 1 2 label text=6
	widget 6 0 1 2 label text=7
	widget 7 0 1 2 label text=8


define loop gonogoarmy
	set source table
	set repeat 1.6
	set order random
	set description "Repeatedly runs another item"
	set cycles 32
	set continuous no
	set break_if_on_first yes
	set break_if never
	setcycle 0 Role1 ARMY
	setcycle 0 Role2 ARMY
	setcycle 0 correct_response None
	setcycle 1 Role1 ARMY
	setcycle 1 Role2 CIVIL
	setcycle 1 correct_response None
	setcycle 2 Role1 ARMY
	setcycle 2 Role2 POLICE
	setcycle 2 correct_response None
	setcycle 3 Role1 CIVIL
	setcycle 3 Role2 CIVIL
	setcycle 3 correct_response None
	setcycle 4 Role1 CIVIL
	setcycle 4 Role2 NEUTRAL
	setcycle 4 correct_response None
	setcycle 5 Role1 NEUTRAL
	setcycle 5 Role2 CIVIL
	setcycle 5 correct_response None
	setcycle 6 Role1 NEUTRAL
	setcycle 6 Role2 NEUTRAL
	setcycle 6 correct_response None
	setcycle 7 Role1 NEUTRAL
	setcycle 7 Role2 POLICE
	setcycle 7 correct_response None
	setcycle 8 Role1 NEUTRAL
	setcycle 8 Role2 TERRORIST
	setcycle 8 correct_response None
	setcycle 9 Role1 POLICE
	setcycle 9 Role2 ARMY
	setcycle 9 correct_response None
	setcycle 10 Role1 POLICE
	setcycle 10 Role2 CIVIL
	setcycle 10 correct_response None
	setcycle 11 Role1 POLICE
	setcycle 11 Role2 POLICE
	setcycle 11 correct_response None
	setcycle 12 Role1 TERRORIST
	setcycle 12 Role2 NEUTRAL
	setcycle 12 correct_response None
	setcycle 13 Role1 ARMY
	setcycle 13 Role2 IMPOSTOR
	setcycle 13 correct_response None
	setcycle 14 Role1 ARMY
	setcycle 14 Role2 NEUTRAL
	setcycle 14 correct_response None
	setcycle 15 Role1 IMPOSTOR
	setcycle 15 Role2 ARMY
	setcycle 15 correct_response None
	setcycle 16 Role1 IMPOSTOR
	setcycle 16 Role2 IMPOSTOR
	setcycle 16 correct_response space
	setcycle 17 Role1 TERRORIST
	setcycle 17 Role2 TERRORIST
	setcycle 17 correct_response space
	setcycle 18 Role1 IMPOSTOR
	setcycle 18 Role2 TERRORIST
	setcycle 18 correct_response space
	setcycle 19 Role1 ARMY
	setcycle 19 Role2 TERRORIST
	setcycle 19 correct_response space
	setcycle 20 Role1 CIVIL
	setcycle 20 Role2 IMPOSTOR
	setcycle 20 correct_response space
	setcycle 21 Role1 CIVIL
	setcycle 21 Role2 TERRORIST
	setcycle 21 correct_response space
	setcycle 22 Role1 IMPOSTOR
	setcycle 22 Role2 CIVIL
	setcycle 22 correct_response space
	setcycle 23 Role1 IMPOSTOR
	setcycle 23 Role2 NEUTRAL
	setcycle 23 correct_response space
	setcycle 24 Role1 IMPOSTOR
	setcycle 24 Role2 POLICE
	setcycle 24 correct_response space
	setcycle 25 Role1 NEUTRAL
	setcycle 25 Role2 IMPOSTOR
	setcycle 25 correct_response space
	setcycle 26 Role1 POLICE
	setcycle 26 Role2 IMPOSTOR
	setcycle 26 correct_response space
	setcycle 27 Role1 POLICE
	setcycle 27 Role2 TERRORIST
	setcycle 27 correct_response space
	setcycle 28 Role1 TERRORIST
	setcycle 28 Role2 ARMY
	setcycle 28 correct_response space
	setcycle 29 Role1 TERRORIST
	setcycle 29 Role2 CIVIL
	setcycle 29 correct_response space
	setcycle 30 Role1 TERRORIST
	setcycle 30 Role2 IMPOSTOR
	setcycle 30 correct_response space
	setcycle 31 Role1 TERRORIST
	setcycle 31 Role2 POLICE
	setcycle 31 correct_response space
	run gonogoarmy_play

define sequence gonogoarmy_play
	set flush_keyboard yes
	set description "Runs a number of items in sequence"
	run fixation always
	run target always
	run new_keyboard_response always
	run right_1 "[correct] = 1"
	run wrong_1 "[correct] = 0"
	run rightsound "[correct] = 1"
	run wrongsound "[correct] = 0"
	run log_score always

define inline_javascript inline_capacity
	set description "Executes JavaScript code"
	___run__
	// computes response time
	vars.response_time = vars.time_score_response - vars.time_digit
	
	// computes score
	if (vars.response==vars.correct_response) {
	vars.correct = 1
	vars.total += 1
	} else {
	vars.correct = 0
	}
	__end__
	set _prepare ""

define inline_javascript inline_varstotal
	set description "Executes JavaScript code"
	set _run "vars.total=0"
	set _prepare ""

define keyboard_response key_energy
	set timeout "[time]"
	set flush yes
	set event_type keypress
	set duration keypress
	set description "Collects keyboard responses"
	set allowed_responses "1;2;3;4;5;6;7;8;9;0;space"

define keyboard_response key_time
	set timeout "[time]"
	set flush yes
	set event_type keypress
	set duration keypress
	set description "Collects keyboard responses"
	set allowed_responses "1;2;space"

define logger log_score
	set description "Logs experimental data"
	set auto_log no
	log accuracy
	log avg_rt
	log correct
	log correct_key_time
	log correct_response
	log count_experiment
	log dis_pos
	log form_response
	log response
	log response_key_energy
	log response_key_time
	log response_time
	log subject_nr
	log subject_parity
	log test_session
	log total_correct
	log total

define feedback new_feedback
	set reset_variables yes
	set duration keypress
	set description "Provides feedback to the participant"
	draw textline center=1 color=black font_bold=yes font_family=arabic font_italic=no font_size=26 html=yes show_if=always text="Selamat!<br /><br />Skor anda : [total_correct]/50<br />Tingkat Akurasi : [acc]%<br />Rerata waktu respon: [avg_rt] milidetik<br /><br /><br />Terimakasih telah berpartisipasi!<br />Klik Spasi untuk menuju tes berikutnya!" x=-13.0 y=-32.0 z_index=0

define form_text_input new_form_text_input
	set timeout infinite
	set spacing 10
	set rows "1;1;6"
	set only_render no
	set margins "50;50;50;50"
	set form_var response
	set form_title "Identitas Responden"
	set form_question "Silakan Ketik Nama/ID/Inisial Anda, kemudian klik Enter"
	set description "A simple text input form"
	set cols 1
	set _theme gray
	widget 0 0 1 1 label text="[form_title]"
	widget 0 1 1 1 label center=no text="[form_question]"
	widget 0 2 1 1 text_input focus=yes return_accepts=yes stub="" var="[form_var]"


define keyboard_response new_keyboard_response
	set timeout 500
	set flush no
	set event_type keypress
	set duration keypress
	set description "Collects keyboard responses"
	set allowed_responses "space;None"

define sketchpad pad_aba2
	set duration "[durasi]"
	set description "Displays stimuli"
	draw textline center=1 color="[color]" font_bold=no font_family=arabic font_italic=no font_size=60 html=yes show_if=always text="[abaaba]" x=0 y=0 z_index=0

define sketchpad pad_capacity
	set start_response_interval no
	set reset_variables no
	set duration "[WAKTU]"
	set description "Displays stimuli"
	draw textline center=1 color=black font_bold=yes font_family=serif font_italic=no font_size=20 html=yes show_if=always text="Ingat gambar berikut ini!" x=0 y=-320 z_index=0
	draw image center=1 file="[S1].png" scale=0.5 show_if=always x="[G1X]" y="[G1Y]" z_index=0
	draw image center=1 file="[S2].png" scale=0.5 show_if=always x="[G2X]" y="[G2Y]" z_index=0
	draw image center=1 file="[S3].png" scale=0.5 show_if=always x="[G3X]" y="[G3Y]" z_index=0
	draw image center=1 file="[S4].png" scale=0.5 show_if=always x="[G4X]" y="[G4Y]" z_index=0
	draw image center=1 file="[S5].png" scale=0.5 show_if=always x="[G5X]" y="[G5Y]" z_index=0
	draw image center=1 file="[S6].png" scale=0.5 show_if=always x="[G6X]" y="[G6Y]" z_index=0
	draw image center=1 file="[S7].png" scale=0.5 show_if=always x="[G7X]" y="[G7Y]" z_index=0
	draw image center=1 file="[S8].png" scale=0.5 show_if=always x="[G8X]" y="[G8Y]" z_index=0

define sketchpad pad_energy
	set duration 0
	set description "Displays stimuli"
	draw image center=1 file="[stim].png" rotation=30 scale=0.7 show_if=always x=0 y=-32 z_index=0
	draw textline center=1 color=black font_bold=yes font_family=arabic font_italic=no font_size=25 html=yes show_if=always text="[dialog]" x=0 y=256 z_index=0
	draw textline center=1 color=black font_bold=yes font_family=arabic font_italic=no font_size=25 html=yes show_if=always text="[dialog2]" x=0 y=288 z_index=0

define sketchpad pad_time
	set duration 0
	set description "Displays stimuli"
	draw image center=1 file="[shape_target].png" scale=0.65 show_if=always x="[tar_pos]" y="[y]" z_index=0
	draw image center=1 file="[shape_distractor].png" scale=0.65 show_if=always x="[dis_pos]" y="[y]" z_index=0
	draw textline center=1 color=black font_bold=yes font_family=arabic font_italic=no font_size=25 html=yes show_if=always text="[dialog]" x=0 y=-288 z_index=0
	draw textline center=1 color=black font_bold=yes font_family=arabic font_italic=no font_size=25 html=yes show_if=always text="[dialog2]" x=0 y=-256 z_index=0
	draw image center=1 file="key1.png" scale=0.15 show_if=always x=-96 y=300 z_index=0
	draw image center=1 file="key2.png" scale=0.15 show_if=always x=96 y=300 z_index=0

define sampler right
	set volume 1
	set stop_after 0
	set sample "right.wav"
	set pitch 1
	set pan 0
	set fade_in 0
	set duration 250
	set description "Plays a sound file in .wav or .ogg format"

define sketchpad right_1
	set duration 208
	set description "Displays stimuli"
	draw image center=1 file="right.png" scale=0.5000000000000001 show_if=always x=0 y=0 z_index=0
	draw textline center=1 color=green font_bold=yes font_family=sans font_italic=no font_size=18 html=yes show_if=always text="Misi Berhasil" x=0 y=-160 z_index=0

define sampler rightsound
	set volume 1
	set stop_after 0
	set sample "Ting-Popup_Pixels-349896185.wav"
	set pitch 1
	set pan 0
	set fade_in 0
	set duration sound
	set description "Plays a sound file in .wav or .ogg format"

define sketchpad salah
	set duration 250
	set description "Displays stimuli"
	draw textline center=1 color=black font_bold=yes font_family=arabic font_italic=no font_size=25 html=yes show_if=always text="Konsentrasi Lagi!" x=0 y=160 z_index=0
	draw image center=1 file="incorrect.png" scale=0.09 show_if=always x=0 y=0 z_index=0

define sequence seq_capacity
	set flush_keyboard yes
	set description "Runs a number of items in sequence"
	run pad_capacity always
	run form_capacity always
	run inline_capacity always
	run benar "[correct]=1"
	run right "[correct]=1"
	run wrong "[correct]=0"
	run salah "[correct]=0"
	run telat "[correct]=0 and [response_time] > 50000"

define sequence seq_energy
	set flush_keyboard yes
	set description "Runs a number of items in sequence"
	run pad_energy always
	run key_energy always
	run benar "[correct]=1"
	run right "[correct]=1"
	run wrong "[correct]=0"
	run salah "[correct]=0"
	run telat "[correct]=0 and [response_time] > 1499"
	run log_score always

define sequence seq_time
	set flush_keyboard yes
	set description "Runs a number of items in sequence"
	run pad_time always
	run key_time always
	run benar "[correct]=1"
	run right "[correct]=1"
	run wrong "[correct]=0"
	run salah "[correct]=0"
	run telat "[correct]=0 and [response_time] > 1195"
	run log_score always

define sketchpad target
	set start_response_interval no
	set reset_variables no
	set duration 500
	set description "Displays stimuli"
	draw image center=1 file="[Role1].png" scale=0.5 show_if=always x=-256 y=-32 z_index=0
	draw image center=1 file="[Role2].png" scale=0.5 show_if=always x=256 y=-32 z_index=0
	draw image center=1 file="button.png" scale=0.2 show_if=always x=0 y=256 z_index=0
	draw textline center=1 color=black font_bold=yes font_family=sans font_italic=no font_size=18 html=yes show_if=always text="T E M B A K" x=0 y=192 z_index=0

define sketchpad telat
	set duration 495
	set description "Displays stimuli"
	draw textline center=1 color=red font_bold=yes font_family=arabic font_italic=no font_size=25 html=yes show_if=always text="Kamu Terlambat Merespon" x=32 y=128 z_index=0
	draw image center=1 file="times up.png" scale=0.30000000000000016 show_if=always x=0 y=0 z_index=0

define sketchpad wait
	set duration 1000
	set description "Displays stimuli"
	draw textline center=1 color=black font_bold=no font_family=serif font_italic=no font_size=30 html=yes show_if=always text="Mohon menunggu..." x=0 y=0 z_index=0

define sketchpad welcome
	set start_response_interval no
	set reset_variables no
	set duration keypress
	set description "Displays stimuli"
	draw textline center=1 color="#ffffff" font_bold=no font_family=serif font_italic=no font_size=32 html=yes show_if=always text="Klik Spasi untuk Memulai!" x=-32 y=352 z_index=0
	draw textline center=1 color="#ffffff" font_bold=yes font_family=serif font_italic=no font_size=20 html=yes show_if=always text="Klik 'Spasi' untuk memulai Tes!" x=0 y=224 z_index=0
	draw image center=1 file="welcomepage.png" scale=1 show_if=always x=0 y=0 z_index=0

define sampler wrong
	set volume 1
	set stop_after 0
	set sample "wrong.wav"
	set pitch 1
	set pan 0
	set fade_in 0
	set duration sound
	set description "Plays a sound file in .wav or .ogg format"

define sketchpad wrong_1
	set duration 208
	set description "Displays stimuli"
	draw image center=1 file="wrong.png" scale=0.5000000000000001 show_if=always x=0 y=0 z_index=0
	draw textline center=1 color=red font_bold=yes font_family=sans font_italic=no font_size=18 html=yes show_if=always text="Target Salah!" x=0 y=-160 z_index=0

define sampler wrongsound
	set volume 1
	set stop_after 0
	set sample "Windows Critical Stop.wav"
	set pitch 1
	set pan 0
	set fade_in 0
	set duration sound
	set description "Plays a sound file in .wav or .ogg format"


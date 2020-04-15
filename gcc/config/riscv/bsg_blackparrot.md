(define_automaton "bsg_blackparrot")

;; EXE stage functional units, FPU has 3-stage pipeline
(define_cpu_unit "bsg_blackparrot_alu" "bsg_blackparrot")
(define_cpu_unit "bsg_blackparrot_div" "bsg_blackparrot")

(define_insn_reservation "bsg_blackparrot_alu" 1
  (and (eq_attr "tune" "bsg_blackparrot")
       (eq_attr "type" "unknown,arith,shift,slt,multi,logical,move,nop,auipc,const"))
  "bsg_blackparrot_alu")

(define_insn_reservation "bsg_blackparrot_branch" 1
  (and (eq_attr "tune" "bsg_blackparrot")
       (eq_attr "type" "branch"))
  "bsg_blackparrot_alu")

(define_insn_reservation "bsg_blackparrot_jump" 1
  (and (eq_attr "tune" "bsg_blackparrot")
       (eq_attr "type" "jump,call"))
  "bsg_blackparrot_alu")

(define_insn_reservation "bsg_blackparrot_load" 2
  (and (eq_attr "tune" "bsg_blackparrot")
       (eq_attr "type" "load,fpload"))
  "bsg_blackparrot_alu")

(define_insn_reservation "bsg_blackparrot_store" 1
  (and (eq_attr "tune" "bsg_blackparrot")
       (eq_attr "type" "store,fpstore"))
  "bsg_blackparrot_alu")

(define_insn_reservation "bsg_blackparrot_imul" 4
  (and (eq_attr "tune" "bsg_blackparrot")
       (eq_attr "type" "imul"))
  "bsg_blackparrot_alu")

(define_insn_reservation "bsg_blackparrot_idiv" 34
  (and (eq_attr "tune" "bsg_blackparrot")
       (eq_attr "type" "idiv"))
  "bsg_blackparrot_div*34")

(define_insn_reservation "bsg_blackparrot_floats" 5
  (and (eq_attr "tune" "bsg_blackparrot")
       (eq_attr "type" "fadd,fmul,fdiv,fcvt,fcmp,fmove"))
  "bsg_blackparrot_alu")

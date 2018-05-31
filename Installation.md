# Update
sudo apt-get update

# Install Emacs
sudo apt-get install -y emacs24

# Install Haskell
sudo apt-get install -y software-properties-common
sudo add-apt-repository -y ppa:hvr/ghc
sudo apt-get update
sudo apt-get install -y cabal-install-1.22 ghc-7.10.3
cat >> ~/.bashrc <<EOF
export PATH="\$HOME/.cabal/bin:/opt/cabal/1.22/bin:/opt/ghc/7.10.3/bin:\$PATH"
EOF
export PATH=~/.cabal/bin:/opt/cabal/1.22/bin:/opt/ghc/7.10.3/bin:$PATH

# Install Agda
sudo apt-get install -y zlib1g-dev libncurses5-dev alex-3.1.7 happy-1.19.5 texlive-binaries
cabal update
cabal install alex-3.1.7 happy-1.19.5 cpphs-1.20.2 agda-2.5.2

# Checkout generic-reuse repository
sudo apt-get install -y git
cd ~
git clone https://github.com/larrytheliquid/generic-reuse.git
cd generic-reuse
git checkout -b artifact

# Install Cedille
cd cedille-prerelease
make

# Set Cedille Options
mkdir ~/.cedille
ln -s ~/generic-reuse/code/options ~/.cedille/options
# update PATH-TO-CHECKOUT in ~/.cedille/options to point
# to your absolute generic-reuse checkout path

# Setup Cedille Mode for Emacs in your init.el
# (setq cedille-path "/PATH-TO-CHECKOUT/generic-reuse/cedille-prerelease")
# (add-to-list 'load-path cedille-path)
# (require 'cedille-mode)


# Now read ~/generic-reuse/ArtifactOverview.md
# for instructions on how to evaluate this artifact.

